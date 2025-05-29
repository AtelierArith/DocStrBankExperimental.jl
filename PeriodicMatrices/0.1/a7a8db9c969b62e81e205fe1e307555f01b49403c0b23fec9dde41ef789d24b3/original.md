```
SwitchingPeriodicMatrix(M, ns, T; nperiod = k) -> A::SwitchingPeriodicMatrix
```

Discrete-time switching periodic matrix representation.

The discrete-time switching periodic matrix object `A` is built from a  `p`-vector `M` of real matrices, a `p`-vector `ns` of increasing positive integers representing the discrete switching moments,  the associated time period `T` and  the number of subperiods specified via the keyword argument `nperiod = k`. 

`M` contains the component matrices `M[i]`, `i = 1,..., p`, which defines  a sequence of `N := ns[p]` of matrices `S[1], ..., S[N]`,  such that `S[j] = M[i]` for `j ∈ [ns[i-1]+1, ..., ns[i]]` with `ns[0] := 0`. `S[j]` is the `j`-th value `A(Δ(j-1))` of a time periodic matrix `A(t)` of subperiod `T′ := T/k`, with `Δ := T′/N`, the associated sample time.  All component matrices are allowed to have arbitrary (time-varying) dimensions. The component matrices `M`, the integer vector `ns`, the period `T`,  the number of subperiods `k`, the discrete period `N`  and the sample time `Δ` can be accessed via `A.M`, `A.ns`, `A.period`, `A.nperiod`, `A.dperiod` and `A.Ts`, respectively. 

The j-th time value `A(Δ(j-1))` can be determined as `A[j]`.  It is assumed that `A[j] := A[mod(j-1,N)+1]` for arbitrary `j`. 
