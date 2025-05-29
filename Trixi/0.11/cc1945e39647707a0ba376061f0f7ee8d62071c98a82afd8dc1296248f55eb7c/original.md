```
VolumeIntegralUpwind(splitting)
```

Specialized volume integral for finite difference summation-by-parts (FDSBP) solvers. Can be used together with the upwind SBP operators of Mattsson (2017) implemented in SummationByPartsOperators.jl. The `splitting` controls the discretization.

See also [`splitting_steger_warming`](@ref), [`splitting_lax_friedrichs`](@ref), [`splitting_vanleer_haenel`](@ref).

## References

  * Mattsson (2017) Diagonal-norm upwind SBP operators [doi: 10.1016/j.jcp.2017.01.042](https://doi.org/10.1016/j.jcp.2017.01.042)

!!! warning "Experimental implementation (upwind SBP)"
    This is an experimental feature and may change in future releases.

