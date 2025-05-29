```
PeriodicFunctionMatrix(f, T; nperiod = k) -> A::PeriodicFunctionMatrix
```

Continuous-time periodic function matrix representation.

The continuous-time periodic function matrix object `A` is built from the real matrix function `f(t)` of real time variable `t`,  the associated time period `T` and the associated number of subperiods specified via the keyword argument `nperiod = k`.  It is assumed that  `f(t) = f(t+T/k)` for any real time value `t`. The function `f(t)`, the period `T`, the row and column dimensions  of `f(t)`, the number of subperiods `k` can be accessed via `A.f`, `A.period`,  the tuple `A.dims` and `A.nperiod`, respectively. 
