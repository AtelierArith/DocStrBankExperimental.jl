```
splitting_coirier_vanleer(u, orientation::Integer,
                          equations::CompressibleEulerEquations1D)
splitting_coirier_vanleer(u, which::Union{Val{:minus}, Val{:plus}}
                          orientation::Integer,
                          equations::CompressibleEulerEquations1D)
```

Splitting of the compressible Euler flux from Coirier and van Leer. The splitting has correction terms in the pressure splitting as well as the mass and energy flux components. The motivation for these corrections are to handle flows at the low Mach number limit.

Returns a tuple of the fluxes "minus" (associated with waves going into the negative axis direction) and "plus" (associated with waves going into the positive axis direction). If only one of the fluxes is required, use the function signature with argument `which` set to `Val{:minus}()` or `Val{:plus}()`.

!!! warning "Experimental implementation (upwind SBP)"
    This is an experimental feature and may change in future releases.


## References

  * William Coirier and Bram van Leer (1991) Numerical flux formulas for the Euler and Navier-Stokes equations. II - Progress in flux-vector splitting [DOI: 10.2514/6.1991-1566](https://doi.org/10.2514/6.1991-1566)
