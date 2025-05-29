```
get_potential_intensity_of_tropical_cyclone(sea_surface_temp <: Real,
sea_surface_pressure <: Real, 
pressure :: Array{<: Real}, 
temperature :: Array{<: Real},
 mixing_ratio :: Array{<: Real}; 
ckovercd = 0.9, reversible_ascent=1, dissipative_heating = true)
```

Compute the minimum pressure at the center and the maximum wind speed of a tropical cyclone using Emanuel's potential intensity theory.
