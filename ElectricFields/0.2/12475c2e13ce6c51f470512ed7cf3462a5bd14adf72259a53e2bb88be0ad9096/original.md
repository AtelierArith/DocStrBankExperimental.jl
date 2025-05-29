```
IsotropicMedium(material, d[, ∂k∂ω₀ = 0])
```

Describes the dispersion through an isotropic medium of thickness `d` (such as an atomic gas), where the refractive index, given by `material`, is the same in all directions.

The optional `∂k∂ω₀` can be used to subtract the linear slope from the dispersion relation, i.e. remove the time shift, such that a pulse with central angular frequency `ω₀` stays centred in the frame of reference.
