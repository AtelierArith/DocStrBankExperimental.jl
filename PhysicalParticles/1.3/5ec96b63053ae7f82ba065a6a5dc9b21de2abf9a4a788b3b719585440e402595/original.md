```
rotate_y(p::PVector, pitch::Number)
```

Rotate `p` around y-axis by `pitch` in radian angle. The rotation direction is right-handed, which is counter-clockwise in y-z plane. Angles can have units, for example, u"°" (\degree).

The rotation matrix:

```
            |  cos(pitch)   0   sin(pitch) |
Ry(pitch) = |       0       1        0     |
            | -sin(pitch)   0   cos(pitch) |
```
