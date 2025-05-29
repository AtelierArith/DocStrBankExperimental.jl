```
setspace(zmin::Real, zmax::Real, rotation::Int, tilt::Int)
```

Set the abstract Z-space used for mapping three-dimensional output primitives into the current world coordinate space.

**Parameters:**

`zmin` :     Minimum value for the Z-axis. `zmax` :     Maximum value for the Z-axis. `rotation` :     Angle for the rotation of the X axis, in degrees. `tilt` :     Viewing angle of the Z axis in degrees.

`setspace` establishes the limits of an abstract Z-axis and defines the angles for rotation and for the viewing angle (tilt) of a simulated three-dimensional graph, used for mapping corresponding output primitives into the current window. These settings are used for all subsequent three-dimensional output primitives until other values are specified. Angles of rotation and viewing angle must be specified between 0° and 90°.
