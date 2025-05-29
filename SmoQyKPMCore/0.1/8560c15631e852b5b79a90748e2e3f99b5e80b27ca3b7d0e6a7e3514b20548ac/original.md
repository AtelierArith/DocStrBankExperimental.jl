```
kpm_update!(
    kpm_expansion::KPMExpansion{T}, func::Function, bounds, M::Int, N::Int = 2*M
) where {T<:AbstractFloat}
```

In-place update an instance of [`KPMExpansion`](@ref) to reflect new values for eigenspectrum `bounds`, expansion order `M`, and number of points at which the expanded function is evaluated when computing the expansion coefficients. This includes recomputing the expansion coefficients.
