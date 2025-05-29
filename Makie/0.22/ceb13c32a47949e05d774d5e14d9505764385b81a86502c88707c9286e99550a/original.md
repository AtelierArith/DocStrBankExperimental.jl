```
origin!([mode = Absolute], t::Transformable, xyz...)
origin!([mode = Absolute], t::Transformable, xyz::VecTypes)
```

Sets the origin of the transformable `t` to the given `xyz` value. This affects the origin of `rotate!(t, ...)` and `scale!(t, ...)`. If `mode` is given as `Accum` the origin is translated by the given `xyz` instead.
