```
 text3D(str, anchor::Point3D;
    halign=:left,
    valign=:baseline,
    about=Point3D(0., 0., 0.),
    rotation::Rotation=RotXYZ(0, 0, 0))
```

Draw text at point `pt`, lying in the plane of the x axis. Angles in `rotation` rotate the text about the `about` point, defaulting to `Point3D(0, 0, 0)`.

Uses Luxor's `fontface()` and `fontsize()` settings.

Specify rotations using functions from Rotations.jl, such as:

  * `RotX(a)`
  * `RotZ(a)`
  * `RotXZ(a1, a2)`
  * `RotXYZ(a1, a2, a3)`
