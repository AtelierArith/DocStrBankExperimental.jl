```
pl_interpolate(prob, T, u, x, y)
```

Given a `prob <: AbstractFVMProblem`, a triangle `T` containing a point `(x, y)`,  and a set of function values `u` at the corresponding nodes of `prob`, interpolates  the solution at the point `(x, y)` using piecewise linear interpolation.
