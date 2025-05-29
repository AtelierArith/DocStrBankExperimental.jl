```
Crystal(material, d, R[, ∂k∂ω₀ = 0])
```

Describes the dispersion through a general crystal of thickness `d` and orientation given by the rotation `R`, with different refractive indices, given by the components of `material`, along the different crystal axes.

In the special case where `material` has two components, we have a *uniaxial* crystal, which is birefringent, and `material[1]` is referred to as *ordinary* the refractive index, and `material[2]` as the *extraordinary* refractive index.

The optional `∂k∂ω₀` can be used to subtract the linear slope from the dispersion relation, i.e. remove the time shift, such that a pulse with central angular frequency `ω₀` stays centred in the frame of reference.
