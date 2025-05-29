```
PeriodicMatrix(M, T; nperiod = k) -> A::PeriodicMatrix
```

Discrete-time periodic matrix representation. 

The discrete-time periodic matrix object `A` is built from a  `p`-vector `M` of real matrices, the associated time period `T` and  the number of subperiods specified via the keyword argument `nperiod = k`. 

`M` contains the cyclic component matrices `M[i]`, `i = 1,..., p`,  where `M[i]` represents the value `M(Δ(i-1))` of a time periodic matrix `M(t)` of period `T/k`, with `Δ := T/(k*p)`, the associated sample time.  It is assumed that `M[i] := M[mod(i-1,p)+1]` for arbitrary `i`.  All component matrices are allowed to have arbitrary (time-varying) dimensions. The component matrices `M`, the period `T`, the number of subperiods `k`, the discrete period `p`  and the sample time `Δ` can be accessed via `A.M`, `A.period`, `A.nperiod`, `A.dperiod` and `A.Ts`, respectively. 
