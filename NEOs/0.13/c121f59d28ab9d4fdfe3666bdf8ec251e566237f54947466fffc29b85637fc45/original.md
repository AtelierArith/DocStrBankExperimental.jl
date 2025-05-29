```
tryls(res::AbstractVector{OpticalResidual{T, TaylorN{T}}},
    x0::Vector{T} [, idxs::AbstractVector{Int}]; kwargs...) where {T <: Real}
```

Try the least squares minimization of the normalized mean square residual of `res`, starting from initial guess `x0`. If `idxs` (default: `eachindex(x0)`) is given, perform the minimization over a subset of the parameters.

See also [`LeastSquaresCache`](@ref), [`AbstractLeastSquaresMethod`](@ref), [`_lsmethods`](@ref) and [`leastsquares!`](@ref).

## Keyword Arguments

  * `maxiter::Int`: maximum number of iterations (default: `25`).
  * `cache::LeastSquaresCache{T}`: least squares cache (default:   `LeastSquaresCache(x0, idxs, maxiter)`).
  * `methods::Vector{AbstractLeastSquaresMethod}`: least squares routines to try   (default: `_lsmethods(res, x0, idxs)`).
