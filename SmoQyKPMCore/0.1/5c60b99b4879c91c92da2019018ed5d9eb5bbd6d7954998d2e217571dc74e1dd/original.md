```
kpm_update_bounds!(
    kpm_expansion::KPMExpansion{T}, func::Function, bounds
) where {T<:AbstractFloat}
```

In-place update an instance of [`KPMExpansion`](@ref) to reflect new values for eigenspectrum `bounds`, recomputing the expansion coefficients.
