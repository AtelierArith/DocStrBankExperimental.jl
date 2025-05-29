```
Pressure(; max_abs = nothing, max_rel = 0.2, scale = si_unit(:bar), maximum = Inf, minimum = DEFAULT_MINIMUM_PRESSURE)
```

Pressure variable definition. `max_abs`/`max_rel` maximum allowable absolute/relative change over a Newton iteration, `scale` is a "typical" value used to regularize the linear system, `maximum` the largest possible value and `minimum` the smallest.
