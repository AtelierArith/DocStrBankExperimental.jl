```
specificenthalpy(h::Real=0,W::Weather) = specificenthalpy(temperature(h,W),fluid(W))
```

Specific enthalpy `h` at altitude of `Weather` location (J⋅kg⁻¹ or ft⋅lb⋅slug⁻¹).
