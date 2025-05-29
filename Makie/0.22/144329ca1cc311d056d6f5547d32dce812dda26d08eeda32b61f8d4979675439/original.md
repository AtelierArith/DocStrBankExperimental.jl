```
translate_cam!(scene, cam::Camera3D, v::Vec3)
```

Translates the camera by the given vector in camera space, i.e. by `v[1]` to the right, `v[2]` to the top and `v[3]` forward.

Note that this method reacts to `fix_x_key` etc. If any of those keys are pressed the translation will be restricted to act in these directions.
