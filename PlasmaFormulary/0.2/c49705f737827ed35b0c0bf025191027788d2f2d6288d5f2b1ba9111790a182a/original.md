```
Alfven_speed(B::BField, ρ)
Alfven_speed(𝐁::Vector{BField}, ρ)
Alfven_speed(B::BField, n::NumberDensity, mass_number = 1)
Alfven_speed(𝐁::Vector{BField}, n::NumberDensity, mass_number = 1)
```

Alfvén speed $V_A$, the typical propagation speed of magnetic disturbances in a quasineutral plasma.

Note that this is different from the Alfven velocity, see also [`Alfven_velocity`](@ref). References: [PlasmaPy API Documentation](https://docs.plasmapy.org/en/stable/api/plasmapy.formulary.speeds.Alfven_speed.html)
