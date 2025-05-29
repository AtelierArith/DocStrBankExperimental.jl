```
rotate_x(p::PVector, roll::Number)
```

Rotate `p` around x-axis by `roll` in radian angle. The rotation direction is right-handed, which is counter-clockwise in y-z plane. Angles can have units, for example, u"°" (\degree).

The rotation matrix:

```
           | 1      0          0      |
Rx(roll) = | 0  cos(roll)  -sin(roll) |
           | 0  sin(roll)   cos(roll) |
```
