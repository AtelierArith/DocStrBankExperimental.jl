```
LevenbergMarquardt(res::AbstractVector{OpticalResidual{T, TaylorN{T}}},
    x0::Vector{T}, idxs::AbstractVector{Int}) where {T <: Real}
```

Return a `LevenbergMarquardt{T}` object for least squares minimization.

See also [`leastsquares`](@ref).

## Arguments

  * `res::AbstractVector{OpticalResidual{T, TaylorN{T}}}`: vector of residuals.
  * `x_0::Vector{T}`: initial guess.
  * `idxs::AbstractVector{Int}`: subset of parameters for fit.

!!! reference
    See section 15.5.2 of https://numerical.recipes.

