```
rotate!(t::Transformable, axis_rot::Quaternion)
rotate!(t::Transformable, axis_rot::Real)
rotate!(t::Transformable, axis_rot...)
```

Apply an absolute rotation to the transformable. Rotations are all internally converted to `Quaternion`s.
