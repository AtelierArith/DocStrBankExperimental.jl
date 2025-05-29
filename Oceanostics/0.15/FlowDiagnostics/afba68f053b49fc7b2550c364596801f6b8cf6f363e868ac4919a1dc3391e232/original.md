```julia
ThermalWindPotentialVorticity(model; tracer, location)

```

Calculate the Potential Vorticty assuming thermal wind balance for `model`, where the characteristics of the Coriolis rotation are taken from `model.coriolis`. The Potential Vorticity in this case is defined as

```
    TWPV = (f + ωᶻ) ∂b/∂z - f ((∂U/∂z)² + (∂V/∂z)²)
```

where `f` is the Coriolis frequency, `ωᶻ` is the relative vorticity in the `z` direction, `b` is the buoyancy, and `∂U/∂z` and `∂V/∂z` comprise the thermal wind shear.
