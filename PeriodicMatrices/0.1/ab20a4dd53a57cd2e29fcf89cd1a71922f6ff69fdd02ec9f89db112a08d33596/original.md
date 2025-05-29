```
 monodromy(A::PeriodicTimeSeriesMatrix) -> Ψ::PeriodicArray
```

Compute the monodromy matrix for a continuous-time time series matrix. 

For the given square periodic matrix `A(t)` of period `T` and subperiod `T′ = T/k`, where  `k` is the number of subperiods,   the monodromy matrix `Ψ = Φ(T′,0)` is computed, where `Φ(t,τ)` is the state transition matrix satisfying the homogeneous linear ODE 

```
dΦ(t,τ)/dt = A(t)Φ(t,τ),  Φ(τ,τ) = I.
```

`A` is a [`PeriodicTimeSeriesMatrix`](@ref) with `K` component matices and the resulting monodromy matrix `Ψ`  is stored as a discrete-time periodic array with `K` component matrices, of period `T` and `k` subperiods. 

`Ψ = Φ(T′,0)` is determined as a product of `K` matrices  `Ψ = Ψ_K*...*Ψ_1`, where for `Δ := T′/K`, `Ψ_i = Φ(iΔ,(i-1)Δ)` is the  state transition matrix on the time interval `[(i-1)Δ,iΔ]`.  Each state transition matrix is computed as a matrix exponential  `Φ(iΔ,(i-1)Δ) = exp(A[i]*Δ)`,  where `A[i]` is the `i`-th component matrix of the time series representation.   For large values of `K`, parallel computation of factors can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  
