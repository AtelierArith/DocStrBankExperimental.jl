```
leastsquares(method::LS, res::AbstractVector{OpticalResidual{T, TaylorN{T}}},
    x0::Vector{T} [, idxs::AbstractVector{Int}]; kwargs...) where {LS, T <: Real}
```

Use least squares method `LS` to minimize the normalized mean square residual of `res`, starting from initial guess `x0`. If `idxs` (default: `eachindex(x0)`) is given, perform the minimization over a subset of the parameters.

## Keyword arguments

  * `maxiter::Int`: maximum number of iterations (default: `25`).
