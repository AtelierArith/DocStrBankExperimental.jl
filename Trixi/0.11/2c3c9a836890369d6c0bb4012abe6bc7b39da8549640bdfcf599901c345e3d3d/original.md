```
splitting_vanleer_haenel(u, orientation_or_normal_direction,
                         equations::CompressibleEulerEquations2D)
splitting_vanleer_haenel(u, which::Union{Val{:minus}, Val{:plus}}
                         orientation_or_normal_direction,
                         equations::CompressibleEulerEquations2D)
```

Splitting of the compressible Euler flux from van Leer. This splitting further contains a reformulation due to Hänel et al. where the energy flux uses the enthalpy. The pressure splitting is independent from the splitting of the convective terms. As such there are many pressure splittings suggested across the literature. We implement the 'p4' variant suggested by Liou and Steffen as it proved the most robust in practice. For details on the curvilinear variant of this flux vector splitting see Anderson et al.

Returns a tuple of the fluxes "minus" (associated with waves going into the negative axis direction) and "plus" (associated with waves going into the positive axis direction). If only one of the fluxes is required, use the function signature with argument `which` set to `Val{:minus}()` or `Val{:plus}()`.

!!! warning "Experimental implementation (upwind SBP)"
    This is an experimental feature and may change in future releases.


## References

  * Bram van Leer (1982) Flux-Vector Splitting for the Euler Equation [DOI: 10.1007/978-3-642-60543-7_5](https://doi.org/10.1007/978-3-642-60543-7_5)
  * D. Hänel, R. Schwane and G. Seider (1987) On the accuracy of upwind schemes for the solution of the Navier-Stokes equations [DOI: 10.2514/6.1987-1105](https://doi.org/10.2514/6.1987-1105)
  * Meng-Sing Liou and Chris J. Steffen, Jr. (1991) High-Order Polynomial Expansions (HOPE) for Flux-Vector Splitting [NASA Technical Memorandum](https://ntrs.nasa.gov/citations/19910016425)
  * W. Kyle Anderson, James L. Thomas, and Bram van Leer (1986) Comparison of Finite Volume Flux Vector Splittings for the Euler Equations [DOI: 10.2514/3.9465](https://doi.org/10.2514/3.9465)
