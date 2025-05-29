```
flux_es_ersing_etal(u_ll, u_rr, orientation_or_normal_direction,
                    equations::ShallowWaterTwoLayerEquations1D)
```

Entropy stable surface flux for the two-layer shallow water equations. Uses the entropy conservative  [`flux_wintermeyer_etal`](@ref) and adds a Lax-Friedrichs type dissipation dependent on the jump of  entropy variables. 

For further details see:

  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on  curvilinear meshes [DOI: 10.1007/s10915-024-02451-2](https://doi.org/10.1007/s10915-024-02451-2)
