from spike import PrimeHub, MotorPair, ColorSensor
from spike.control import wait_until, wait_for_seconds
from spike.operator import equal_to
from math import radians

# Initialisierung
hub = PrimeHub()
motor_pair = MotorPair('A', 'B')
motor_pair.set_default_speed(50)
color_sensor = ColorSensor('A')

# Starte Programm
while hub.left_button.is_pressed():
    if color_sensor.get_color() == 'black':
        motor_pair.start(0)  # geradeaus
    elif color_sensor.get_color() == 'white':
        motor_pair.move(-20, 'rotations', 0.9)  # nach links
    else:
        motor_pair.move(30, 'rotations', 0.9)   # nach rechts
