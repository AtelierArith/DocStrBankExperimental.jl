```
rotate_z(p::PVector, yaw::Number)
```

Rotate `p` around z-axis by `yaw` in radian angle. The rotation direction is right-handed, which is counter-clockwise in y-z plane. Angles can have units, for example, u"°" (\degree).

The rotation matrix:

```
          | cos(yaw)  -sin(yaw)  0 |
Rz(yaw) = | sin(yaw)   cos(yaw)  0 |
          |    0          0      1 |
```
