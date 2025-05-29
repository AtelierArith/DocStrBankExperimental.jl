```
specificenergy(T::Real,G::AbstractMole) = heatvolume(T,G)*T
```

Specific energy `e` of ideal gas `specificenthalpy(T,G)-gasconstant(G)*T` (J⋅kg⁻¹ or ft⋅lb⋅slug⁻¹).
