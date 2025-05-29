```
TaylorInterpolant{T, U, N}
```

Collection of Taylor polynomials that interpolate a dependent variable as a function of an independent variable. For example, the $x$-axis position of the Earth as a function of time $x(t)$; or a lunar core Euler angle as a function of time $\theta_c(t)$.

# Fields

  * `t0::T`: Start time.
  * `t::AbstractVector{T}`: Vector of time instances when the timespan of the $i$-th element of `x` ends and the $(i+1)$-th element of `x` starts being valid.
  * `x::AbstractArray{Taylor1{U},N}`: Array of Taylor polynomials that interpolate the dependent variable as a function of the independent variable.
