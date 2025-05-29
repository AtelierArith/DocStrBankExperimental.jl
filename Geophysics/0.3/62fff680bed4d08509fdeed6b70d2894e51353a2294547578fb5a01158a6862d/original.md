```
enthalpy(T::Real,G::AbstractMole) = heatpressure(T,G)*T
```

Specific enthalpy `h` of ideal gas `specificenergy(T,G)+gasconstant(G)*T` (J⋅kg⁻¹ or ft⋅lb⋅slug⁻¹).
