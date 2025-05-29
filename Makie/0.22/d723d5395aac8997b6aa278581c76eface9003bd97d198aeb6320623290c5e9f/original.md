```
rotate_cam!(scene, cam::Camera3D, angles::Vec3)
```

Rotates the camera by the given `angles` around the camera x- (left, right), y- (up, down) and z-axis (in out). The rotation around the y axis is applied first, then x, then y.

Note that this method reacts to `fix_x_key` etc and `fixed_axis`. The former restrict the rotation around a specific axis when a given key is pressed. The latter keeps the camera y axis fixed as the data space z axis.
