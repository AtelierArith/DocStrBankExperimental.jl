```
specificenergy(F::FluidState) = specificenergy(temperature(F),fluid(F))
```

Specific energy `e` at the temperature of `F` (J⋅kg⁻¹ or ft⋅lb⋅slug⁻¹).
