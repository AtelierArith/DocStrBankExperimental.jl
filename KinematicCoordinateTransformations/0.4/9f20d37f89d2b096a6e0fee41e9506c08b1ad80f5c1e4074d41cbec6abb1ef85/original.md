```
transform(trans::KinematicTransformation, t, x, [v, [a, [j]]], linear_only::Bool=false)
```

Transform vector `x`, and optionally `v`, `a`, and `j` from the source coordinate system to the target coordinate system at time `t` according to the transformation `trans`, returning `x` and optionally `v`, `a`, and `j` in the target coordinate system.

`v`, `a`, and `j` are the first through third time derivatives of `x`.

If `linear_only` is `true`, the constant part (if any) of the transformation will not be applied. For example, with a `ConstantAffineMap`, which represents a transformation of the form `x_target = A*x_source + b`, the `b` will not be used. This is useful for properly transforming vectors that don't represent the position of a point and time derivatives of the same (e.g. force).
