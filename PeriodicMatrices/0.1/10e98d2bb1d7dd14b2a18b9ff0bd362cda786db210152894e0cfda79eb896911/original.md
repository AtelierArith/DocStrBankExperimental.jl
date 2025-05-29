```
PeriodicArray(M, T; nperiod = k) -> A::PeriodicArray
```

Discrete-time periodic array representation.

The discrete-time periodic array object `A` is built from a `m×n×p` real array `M`, the associated time period `T` and the number of subperiods specified via  the keyword argument `nperiod = k`.  `M` contains the cyclic component matrices `M[:,:,i]`, `i = 1,..., p`,  where `M[:,:,i]` represents the value `M(Δ(i-1))` of a time periodic matrix `M(t)` of period `T/k`, with `Δ := T/(kp)`, the associated sample time.  It is assumed that  `M[:,:,k] := M[:,:,mod(k-1,p)+1]` for arbitrary `k`.  The component matrices `M`, the period `T`, the number of subperiods `k`, the discrete period `p`  and the sample time `Δ` can be accessed via `A.M`, `A.period`, `A.nperiod`, `A.dperiod` and `A.Ts`, respectively. 
