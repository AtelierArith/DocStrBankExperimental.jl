```
compute!(pinv::AbstractPoincareInvariant, points::AbstractMatrix, t::Real=NaN, p=nothing)
```

computes a Poincaré invariant using setup object `pinv`, where `points` represents the image of the curve or surface parameterisation evaluated on some set of points, e.g. a grid.

`t` is the time at which the invariant is evaluated `p` are any user supplied optional arguments. Both `t` and `p` are passed directly to the differential form.

Plan implementations should define a method `compute!(pinv, t::Real, p)`, which acts on the internal points storage `pinv.points`.
