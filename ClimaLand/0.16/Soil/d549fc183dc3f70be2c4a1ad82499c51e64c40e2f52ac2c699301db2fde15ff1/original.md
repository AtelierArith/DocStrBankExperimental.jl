```
ClimaLand.make_compute_jacobian(model::EnergyHydrology{FT}) where {FT}
```

Creates and returns the compute_jacobian! function for the EnergyHydrology model. This updates the contribution for the soil liquid water content only.

Using this Jacobian with a backwards Euler timestepper is equivalent to using the modified Picard scheme of Celia et al. (1990).
