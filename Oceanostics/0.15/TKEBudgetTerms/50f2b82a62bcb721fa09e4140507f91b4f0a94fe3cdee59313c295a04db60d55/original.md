```julia
IsotropicKineticEnergyDissipationRate(
    model;
    U,
    V,
    W,
    location
)

```

Calculate the Viscous Dissipation Rate, defined as

```
ε = 2 ν SᵢⱼSᵢⱼ,
```

where Sᵢⱼ is the strain rate tensor, for a fluid with an isotropic turbulence closure (i.e., a  turbulence closure where ν (eddy or not) is the same for all directions.
