```
PhaseTransitions(FT=Float64,
                 ice_density           = 917,   # kg m⁻³
                 ice_heat_capacity     = 2000,  # J / (kg ᵒC)
                 liquid_density        = 999.8, # kg m⁻³
                 liquid_heat_capacity  = 4186,  # J / (kg ᵒC)
                 reference_latent_heat = 334e3  # J kg⁻³
                 liquidus = LinearLiquidus(FT)) # default assumes psu, ᵒC
```

Return a representation of transitions between the solid and liquid phases of salty water: in other words, the freezing and melting of sea ice.

The latent heat of fusion $ℒ(T)$ (more simply just "latent heat") is a function of temperature $T$ via

$$
ρᵢ ℒ(T) = ρᵢ ℒ₀ + (ρ_ℓ c_ℓ - ρᵢ cᵢ) (T - T₀)    
$$

where $ρᵢ$ is the `ice_density`, $ρ_ℓ$ is the liquid density, $cᵢ$ is the heat capacity of ice, and $c_ℓ$ is the heat capacity of liquid, and $T₀$ is a reference temperature, all of which are assumed constant.

The default `liquidus` assumes that salinity has practical salinity units (psu) and that temperature is degrees Celsius.
