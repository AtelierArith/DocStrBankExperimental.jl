```
ConstantAffineMap
```

A `struct` describing a transformation of the form `x_target = A*x_source + b`, and time derivatives of `x_source`, where `A` and `b` are constant in time.

`ConstantAffineMap`s are typically constructed internally from other `KinematicTransformation`s.
