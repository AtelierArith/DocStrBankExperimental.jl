```
DifferentialCorrections(res::AbstractVector{OpticalResidual{T, TaylorN{T}}},
    x0::Vector{T}, idxs::AbstractVector{Int}) where {T <: Real}
```

Return a `DifferentialCorrections{T}` object for least squares minimization.

See also [`leastsquares`](@ref).

## Arguments

  * `res::AbstractVector{OpticalResidual{T, TaylorN{T}}}`: vector of residuals.
  * `x_0::Vector{T}`: initial guess.
  * `idxs::AbstractVector{Int}`: subset of parameters for fit.

!!! reference
    See sections 5.2 and 5.3 of https://doi.org/10.1017/CBO9781139175371.

