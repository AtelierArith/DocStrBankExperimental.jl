```
flux_fjordholm_etal(u_ll, u_rr, orientation,
                    equations::ShallowWaterEquations1D)
```

Total energy conservative (mathematical entropy for shallow water equations). When the bottom topography is nonzero this should only be used as a surface flux otherwise the scheme will not be well-balanced. For well-balancedness in the volume flux use [`flux_wintermeyer_etal`](@ref).

Details are available in Eq. (4.1) in the paper:

  * Ulrik S. Fjordholm, Siddhartha Mishra and Eitan Tadmor (2011) Well-balanced and energy stable schemes for the shallow water equations with discontinuous topography [DOI: 10.1016/j.jcp.2011.03.042](https://doi.org/10.1016/j.jcp.2011.03.042)
