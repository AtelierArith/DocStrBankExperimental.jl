```
PeriodicSwitchingMatrix(At, ts, T; nperiod = k) -> A::PeriodicSwitchingMatrix
```

Continuous-time periodic switching matrix representation.

The continuous-time periodic switching matrix object `A` of period `T` is built from a  `p`-vector `At` of real matrices, a `p`-vector `ts` of increasingly ordered switching time values with `ts[1] = 0`, and  the associated subperiod `T′ = T/k`, where `k ≥ 1` is the number of subperiods (default: `k = 1`).  `At` contains the cyclic component matrices `At[i]`, `i = 1,..., p`,  where `At[i]` is the constant value of a time periodic matrix `A(t)` of period `T′` for `t ∈ [ts[i],ts[i+1])`, if `i < p`, or `t ∈ [ts[i],T′)`, if `i = p`.  It is assumed that `At[i] := At[mod(i-1,p)+1]` and `ts[i] := ts[mod(i-1,p)+1]` for arbitrary `i`.  All component matrices must have the same dimensions. The component matrices `At`, the switching times `ts`, the period `T` and the number of subperiods `k` can be accessed via `A.values`, `A.ts`, `A.period`, and `A.nperiod`, respectively. 
