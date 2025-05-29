```
kpm_update_order!(
    kpm_expansion::KPMExpansion, func::Function, M::Int, N::Int = 2*M
)
```

In-place update the expansion order `M` for an instance of [`KPMExpansion`](@ref), recomputing the expansion coefficients. It is also possible to udpate the number of point `N` the function `func` is evaluated at to calculate the expansion coefficients.
