```
cross_second_virial(model,T,z)
```

Default units: `[m^3]`

Calculates the second cross virial coefficient (B₁₂) of a binary mixture, using the definition:

```julia
B̄ = x₁^2*B₁₁ + 2x₁x₂B₁₂ + x₂^2*B₂₂
B₁₂ = (B̄ - x₁^2*B₁₁ - x₂^2*B₂₂)/2x₁x₂
```

!!! info "Composition-dependent property"
    The second cross virial coefficient calculated from a equation of state can present a dependency on composition [1], but normally, experiments for obtaining the second virial coefficient are made by mixing the same volume of two gases. you can calculate B12 in this way by using (Clapeyron.equivol*cross*second_virial)[@ref]


## References

1. Jäger, A., Breitkopf, C., & Richter, M. (2021). The representation of cross second virial coefficients by multifluid mixture models and other equations of state. Industrial & Engineering Chemistry Research, 60(25), 9286–9295. [doi:10.1021/acs.iecr.1c01186](https://doi.org/10.1021/acs.iecr.1c01186)
