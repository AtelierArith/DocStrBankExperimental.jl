```
bubble_resonance(radius, depth=0; γ=1.4, p₀=1.013e5, ρ=1022.72, g=9.80665)
```

Compute resonance frequency of a freely oscillating has bubble in water, given:

  * bubble `radius` in meters
  * `depth` of bubble in water in meters
  * gas ratio of specific heats 'γ'
  * atmospheric pressure 'p₀' in Pa
  * density of water 'ρ' in kg/m³
  * acceleration due to gravity 'g' in m/s²

This ignores surface-tension, thermal, viscous and acoustic damping effects, and the pressure-volume relationship is taken to be adiabatic. Implementation based on Medwin & Clay (1998).
