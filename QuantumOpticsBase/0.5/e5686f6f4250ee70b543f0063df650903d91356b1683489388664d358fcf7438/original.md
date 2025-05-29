```
time_shift(op::TimeDependentSum, t0)
```

Shift (translate) a [`TimeDependentSum`](@ref) `op` forward in time (delaying its action) by `t0` units, so that the coefficient functions of time `f(t)` become `f(t-t0)`. Return a new [`TimeDependentSum`](@ref).
