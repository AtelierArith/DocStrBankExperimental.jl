```
viscosity(F::FluidState) = viscosity(temperature(F),fluid(F))
```

流体の温度 `F` における層流動的粘度 `μ` (Pa⋅s または lb⋅s¹⋅ft⁻²)。
