```
 psceigsm(A::PeriodicSymbolicMatrix[, K = 1]; lifting = false, solver, reltol, abstol, dt) -> ce
```

Compute the characteristic exponents of a periodic symbolic matrix.

For a given square continuous-time periodic function matrix `A(t)` of period `T`,  the characteristic exponents `ce` are computed as `log.(ev)/T`,  where  `ev` are the characteristic multipliers (i.e., the eigenvalues of the monodromy matrix of `A(t)`).   For available options see [`pseig(::PeriodicFunctionMatrix)`](@ref). 
