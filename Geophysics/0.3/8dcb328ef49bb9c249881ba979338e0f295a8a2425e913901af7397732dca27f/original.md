```
heatpressure(T::Real,G::AbstractMole) = heatvolume(T,G)+gasconstant(G)
```

Specific heat `cₚ` of ideal gas at constant pressure (J⋅kg⁻¹⋅K⁻¹ or ft⋅lb⋅slug⁻¹⋅°R⁻¹).
