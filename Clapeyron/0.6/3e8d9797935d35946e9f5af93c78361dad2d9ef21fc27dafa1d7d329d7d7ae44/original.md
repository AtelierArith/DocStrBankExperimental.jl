```
second_virial_coefficient(model::EoSModel, T, z=SA[1.])
```

Default units: `[m^3]`

Calculates the second virial coefficient `B`, defined as:

```julia
B = lim(ρ->0)[∂Aᵣ/∂ρ]
```

where `Aᵣ` is the residual helmholtz energy.
