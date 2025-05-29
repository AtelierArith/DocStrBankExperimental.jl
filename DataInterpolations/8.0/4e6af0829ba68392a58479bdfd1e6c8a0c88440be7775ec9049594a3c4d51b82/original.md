```
LinearInterpolationIntInv(u, t, A)
```

It is the interpolation of the inverse of the integral of a `LinearInterpolation`. Can be easily constructed with `invert_integral(A::LinearInterpolation{<:AbstractVector{<:Number}})`

## Arguments

  * `u` : Given by `A.t`
  * `t` : Given by `A.I` (the cumulative integral of `A`)
  * `A` : The `LinearInterpolation` object
