```
FDSBP(D_SBP; surface_integral, volume_integral)
```

Specialization of [`DG`](@ref) methods that uses general summation by parts (SBP) operators from [SummationByPartsOperators.jl](https://github.com/ranocha/SummationByPartsOperators.jl). In particular, this includes classical finite difference (FD) SBP methods. These methods have the same structure as classical DG methods - local operations on elements with connectivity through interfaces without imposing any continuity constraints.

`D_SBP` is an SBP derivative operator from SummationByPartsOperators.jl. The other arguments have the same meaning as in [`DG`](@ref) or [`DGSEM`](@ref).

!!! warning "Experimental implementation (upwind SBP)"
    This is an experimental feature and may change in future releases.

