```
 psceig(A[, K = 1]; lifting = false, solver, reltol, abstol, dt) -> ce
```

Compute the characteristic exponents of a continuous-time periodic matrix.

For a given square continuous-time periodic matrix `A(t)` of period `T`,  the characteristic exponents `ce` are computed as `log.(ev)/T`,  where  `ev` are the characteristic multipliers (i.e., the eigenvalues of the monodromy matrix of `A(t)`).   For available options see [`pseig(::PeriodicFunctionMatrix)`](@ref).  `A` may be given as a [`PeriodicFunctionMatrix`](@ref), a [`HarmonicArray`](@ref), a [`PeriodicSymbolicMatrix`](@ref) or a  [`FourierFunctionMatrix`](@ref).  For a given square discrete-time periodic matrix `A(t)` of discrete period `N`,   the characteristic exponents `ce` are computed as `ev.^-N`. 
