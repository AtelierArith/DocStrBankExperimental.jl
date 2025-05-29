```
specificenthalpy(F::FluidState) = specificenthalpy(temperature(F),fluid(F))
```

Specific enthalpy `h` at the temperature of `F` (J⋅kg⁻¹ or ft⋅lb⋅slug⁻¹).
