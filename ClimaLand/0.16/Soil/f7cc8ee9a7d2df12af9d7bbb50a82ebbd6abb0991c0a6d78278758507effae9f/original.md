```
ClimaLand.make_compute_jacobian(model::RichardsModel{FT}) where {FT}
```

Creates and returns the compute_jacobian! function for RichardsModel. This updates the contribution for the soil liquid water content.

Using this Jacobian with a backwards Euler timestepper is equivalent to using the modified Picard scheme of Celia et al. (1990).
