```
 monodromy(A[, K = 1]; solver, reltol, abstol, dt) -> Ψ::PeriodicArray
```

Compute the monodromy matrix for a linear ODE with periodic time-varying coefficients. 

For the given square periodic matrix `A(t)` of period `T` and subperiod `T′ = T/k`, where  `k` is the number of subperiods,   the monodromy matrix `Ψ = Φ(T′,0)` is computed, where `Φ(t,τ)` is the state transition matrix satisfying the homogeneous linear ODE 

```
dΦ(t,τ)/dt = A(t)Φ(t,τ),  Φ(τ,τ) = I.
```

`A` may be given as a [`PeriodicFunctionMatrix`](@ref), a [`HarmonicArray`](@ref), a [`PeriodicSymbolicMatrix`](@ref) or a  [`FourierFunctionMatrix`](@ref). 

If `K > 1`, then `Ψ = Φ(T′,0)` is determined as a product of `K` matrices  `Ψ = Ψ_K*...*Ψ_1`, where for `Δ := T′/K`, `Ψ_i = Φ(iΔ,(i-1)Δ)` is the  state transition matrix on the time interval `[(i-1)Δ,iΔ]`. 

The state transition matrices `Φ(iΔ,(i-1)Δ)` are computed by integrating numerically the above homogeneous linear ODE.   The ODE solver to be employed can be  specified using the keyword argument `solver`, together with the required relative accuracy `reltol` (default: `reltol = 1.e-3`),  absolute accuracy `abstol` (default: `abstol = 1.e-7`) and/or  the fixed step length `dt` (default: `dt = min(Δ, Δ*K′/100)`) (see [`tvstm`](@ref)).  For large values of `K`, parallel computation of factors can be alternatively performed  by starting Julia with several execution threads.  The number of execution threads is controlled either by using the `-t/--threads` command line argument  or by using the `JULIA_NUM_THREADS` environment variable.  
