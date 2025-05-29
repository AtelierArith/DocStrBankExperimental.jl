```
flux_nonconservative_ersing_etal(u_ll, u_rr, orientation::Integer,
                                 equations::ShallowWaterTwoLayerEquations2D)
flux_nonconservative_ersing_etal(u_ll, u_rr,
                                 normal_direction::AbstractVector,
                                 equations::ShallowWaterTwoLayerEquations2D)
```

Non-symmetric path-conservative two-point volume flux discretizing the nonconservative (source) term that contains the gradient of the bottom topography [`ShallowWaterTwoLayerEquations2D`](@ref) and an additional term that couples the momentum of both layers. 

This is a modified version of [`flux_nonconservative_wintermeyer_etal`](@ref) that gives entropy  conservation and well-balancedness in both the volume and surface when combined with  [`flux_wintermeyer_etal`](@ref).

For further details see:

  * Patrick Ersing, Andrew R. Winters (2023) An entropy stable discontinuous Galerkin method for the two-layer shallow water equations on  curvilinear meshes [DOI: 10.1007/s10915-024-02451-2](https://doi.org/10.1007/s10915-024-02451-2)
