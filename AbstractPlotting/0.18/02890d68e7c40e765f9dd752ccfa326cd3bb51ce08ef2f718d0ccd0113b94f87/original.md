```
scale!(t::Transformable, x, y)
scale!(t::Transformable, x, y, z)
scale!(t::Transformable, xyz)
scale!(t::Transformable, xyz...)
```

Scale the given `Transformable` (a Scene or Plot) to the given arguments. Can take `x, y` or `x, y, z`. This is an absolute scaling, and there is no option to perform relative scaling.
