```
rotate!(scene::Transformable, axis_rot::Quaternion)
rotate!(scene::Transformable, axis_rot::AbstractFloat)
rotate!(scene::Transformable, axis_rot...)
```

Apply an absolute rotation to the Scene. Rotations are all internally converted to `Quaternion`s.
