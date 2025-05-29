```
autosymptr(f, B::AbstractMatrix, [syms=nothing]; atol=0, rtol=sqrt(eps()), maxevals=typemax(Int64), buffer=nothing)
```

Computes the integral of `f` to within the specified tolerances and returns a tuple `(I, E, numevals, rules)` containing the estimated integral, the estimated error, the number of integrand evaluations. The integral on the symmetrized domain needs to be mapped back to the full domain by the caller, since for array-valued integrands this depends on the representation of the integrand under the action of the symmetries.

Note that if a vector buffer is provided to store integrand evaluations, the integrand evaluations will be parallelized and it will be assumed that the integrand is threadsafe.

!!! note "Convergence depends on periodicity"
    If the routine takes a long time to return, double check that the period of the function `f` along the basis vectors in the columns of `B` is consistent.

