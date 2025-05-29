```
splitting_steger_warming(u, orientation::Integer,
                         equations::CompressibleEulerEquations2D)
splitting_steger_warming(u, which::Union{Val{:minus}, Val{:plus}}
                         orientation::Integer,
                         equations::CompressibleEulerEquations2D)
```

Splitting of the compressible Euler flux of Steger and Warming. For curvilinear coordinates use the improved Steger-Warming-type splitting [`splitting_drikakis_tsangaris`](@ref).

Returns a tuple of the fluxes "minus" (associated with waves going into the negative axis direction) and "plus" (associated with waves going into the positive axis direction). If only one of the fluxes is required, use the function signature with argument `which` set to `Val{:minus}()` or `Val{:plus}()`.

!!! warning "Experimental implementation (upwind SBP)"
    This is an experimental feature and may change in future releases.


## References

  * Joseph L. Steger and R. F. Warming (1979) Flux Vector Splitting of the Inviscid Gasdynamic Equations With Application to Finite Difference Methods [NASA Technical Memorandum](https://ntrs.nasa.gov/api/citations/19790020779/downloads/19790020779.pdf)
