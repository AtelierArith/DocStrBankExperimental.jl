```
PeriodicSymbolicMatrix(F, T; nperiod = k) -> A::PeriodicSymbolicMatrix
```

Continuous-time periodic symbolic matrix representation.

The continuous-time periodic symbolic matrix object `A` is built from `F`, a  symbolic real matrix or vector of symbolic variable `t`,  the associated time period `T` and the associated number of subperiods specified via the keyword argument `nperiod = k`.  It is assumed that  `F(t) = F(t+T/k)` for any real time value `t`. The symbolic matrix `F`, the period `T` and the number of subperiods `k`  can be accessed via `A.F`, `A.period` and `A.nperiod`, respectively.
