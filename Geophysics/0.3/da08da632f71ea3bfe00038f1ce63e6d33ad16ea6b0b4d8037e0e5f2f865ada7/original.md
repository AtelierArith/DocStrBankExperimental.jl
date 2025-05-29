```
viscosity(F::FluidState) = viscosity(temperature(F),fluid(F))
```

Laminar dynamic vicsosity `μ` at the temperature of `F` (Pa⋅s or lb⋅s¹⋅ft⁻²).
