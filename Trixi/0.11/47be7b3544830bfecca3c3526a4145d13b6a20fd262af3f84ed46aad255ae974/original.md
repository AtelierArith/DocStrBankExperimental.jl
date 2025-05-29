```
splitting_drikakis_tsangaris(u, orientation_or_normal_direction,
                             equations::CompressibleEulerEquations2D)
splitting_drikakis_tsangaris(u, which::Union{Val{:minus}, Val{:plus}}
                             orientation_or_normal_direction,
                             equations::CompressibleEulerEquations2D)
```

Improved variant of the Steger-Warming flux vector splitting [`splitting_steger_warming`](@ref) for generalized coordinates. This splitting also reformulates the energy flux as in Hänel et al. to obtain conservation of the total temperature for inviscid flows.

Returns a tuple of the fluxes "minus" (associated with waves going into the negative axis direction) and "plus" (associated with waves going into the positive axis direction). If only one of the fluxes is required, use the function signature with argument `which` set to `Val{:minus}()` or `Val{:plus}()`.

!!! warning "Experimental implementation (upwind SBP)"
    This is an experimental feature and may change in future releases.


## References

  * D. Drikakis and S. Tsangaris (1993) On the solution of the compressible Navier-Stokes equations using improved flux vector splitting methods [DOI: 10.1016/0307-904X(93)90054-K](https://doi.org/10.1016/0307-904X(93)90054-K)
  * D. Hänel, R. Schwane and G. Seider (1987) On the accuracy of upwind schemes for the solution of the Navier-Stokes equations [DOI: 10.2514/6.1987-1105](https://doi.org/10.2514/6.1987-1105)
