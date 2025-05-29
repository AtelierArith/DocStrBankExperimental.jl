```
compute_density(JD::Number, u::AbstractArray, eop_data::EopIau1980, AtmosphereType::AtmosphericModelType)
```

Computes the atmospheric density at a point given the date, position, eop_data, and atmosphere type

# Arguments

  * `JD::Number`: The current time of the simulation in Julian days.
  * `u::AbstractArray`: The current state of the simulation.
  * `eop_data::EopIau1980`: The earth orientation parameters.
  * `AtmosphereType::AtmosphericModelType`: The type of atmospheric model used to compute the density. Available    options are Jacchia-Bowman 2008 (JB2008), Jacchia-Roberts 1971 (JR1971), NRL MSIS 2000 (MSIS2000),   Exponential (ExpAtmo), and None (None)

# Returns

  * `rho::Number`: The density of the atmosphere at the provided time and point [kg/m^3].
