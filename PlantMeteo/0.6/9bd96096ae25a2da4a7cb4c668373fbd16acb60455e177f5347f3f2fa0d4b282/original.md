```
psychrometer_constant(P, λ, Cₚ, ε; check=true)
psychrometer_constant(P, λ; check=true)
```

γ, the psychrometer constant, also called psychrometric constant (kPa K−1). See Monteith and Unsworth (2013), p. 222.

# Arguments

  * `P` (kPa): air pressure
  * `λ` ($J\ kg^{-1}$): latent heat of vaporization for water (see [`latent_heat_vaporization`](@ref))
  * `Cₚ` (J kg-1 K-1): specific heat of air at constant pressure ($J\ K^{-1}\ kg^{-1}$)
  * `ε` (Celsius degree): temperature in Celsius degree at 0 Kelvin
  * `check` (Bool): check if P is in the 85-110 kPa earth range

# Note

Cₚ, ε and λ₀ are taken from [`Constants`](@ref) if not provided.

```julia
Tₐ = 20.0

λ = latent_heat_vaporization(Tₐ, λ₀)
psychrometer_constant(100.0, λ)
```

# References

Monteith, John L., et Mike H. Unsworth. 2013. « Chapter 13 - Steady-State Heat Balance: (i) Water Surfaces, Soil, and Vegetation ». In Principles of Environmental Physics (Fourth Edition), edited by John L. Monteith et Mike H. Unsworth, 217‑47. Boston: Academic Press.
