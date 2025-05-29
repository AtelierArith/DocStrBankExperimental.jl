```
prandtl(T::Real,G::AbstractMole) = viscosity(T,G)*heatpressure(T,G)/thermalconductivity(T,G)
```

Prandtl number is the ratio of momentum diffusivity to heat diffusivity (dimensionless).
