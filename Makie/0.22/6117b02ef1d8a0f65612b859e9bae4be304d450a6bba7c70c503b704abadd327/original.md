```
scale!([mode = Absolute], t::Transformable, xyz...)
scale!([mode = Absolute], t::Transformable, xyz::VecTypes)
```

Scale the given `t::Transformable` (a Scene or Plot) to the given arguments `xyz`. Any missing dimension will be scaled by 1. If `mode == Accum` the given scaling will be multiplied with the previous one.
