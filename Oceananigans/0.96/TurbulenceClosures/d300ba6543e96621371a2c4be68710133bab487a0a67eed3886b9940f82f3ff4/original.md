```
RiBasedVerticalDiffusivity([time_discretization = VerticallyImplicitTimeDiscretization(),
                           FT = Float64;]
                           Ri_dependent_tapering = HyperbolicTangentRiDependentTapering(),
                           horizontal_Ri_filter = nothing,
                           minimum_entrainment_buoyancy_gradient = 1e-10,
                           maximum_diffusivity = Inf,
                           maximum_viscosity = Inf,
                           ν₀  = 0.7,
                           κ₀  = 0.5,
                           κᶜᵃ = 1.7,
                           Cᵉⁿ = 0.1,
                           Cᵃᵛ = 0.6,
                           Ri₀ = 0.1,
                           Riᵟ = 0.4,
                           warning = true)
```

Return a closure that estimates the vertical viscosity and diffusivity from "convective adjustment" coefficients `ν₀` and `κ₀` multiplied by a decreasing function of the Richardson number, $Ri$.

# Arguments

  * `time_discretization`: Either `ExplicitTimeDiscretization()` or `VerticallyImplicitTimeDiscretization()`,                        which integrates the terms involving only $z$-derivatives in the                        viscous and diffusive fluxes with an implicit time discretization.                        Default `VerticallyImplicitTimeDiscretization()`.
  * `FT`: Float type; default `Float64`.

# Keyword arguments

  * `Ri_dependent_tapering`: The $Ri$-dependent tapering. Options are: `PiecewiseLinearRiDependentTapering()`, `HyperbolicTangentRiDependentTapering()` (default), and `ExponentialRiDependentTapering()`.
  * `ν₀`: Non-convective viscosity (units of kinematic viscosity, typically m² s⁻¹).
  * `κ₀`: Non-convective diffusivity for tracers (units of diffusivity, typically m² s⁻¹).
  * `κᶜᵃ`: Convective adjustment diffusivity for tracers (units of diffusivity, typically m² s⁻¹).
  * `Cᵉⁿ`: Entrainment coefficient for tracers (non-dimensional).        Set `Cᵉⁿ = 0` to turn off the penetrative entrainment diffusivity.
  * `Cᵃᵛ`: Time-averaging coefficient for viscosity and diffusivity (non-dimensional).
  * `Ri₀`: $Ri$ threshold for decreasing viscosity and diffusivity (non-dimensional).
  * `Riᵟ`: $Ri$-width over which viscosity and diffusivity decreases to 0 (non-dimensional).
  * `minimum_entrainment_buoyancy_gradient`: Minimum buoyancy gradient for application of the entrainment                                          diffusvity. If the entrainment buoyancy gradient is less than the                                          minimum value, the entrainment diffusivity is 0. Units of                                          buoyancy gradient (typically s⁻²).
  * `maximum_diffusivity`: A limiting maximum tracer diffusivity (units of diffusivity, typically m² s⁻¹).
  * `maximum_viscosity`: A limiting maximum viscosity (units of kinematic viscosity, typically m² s⁻¹).
  * `horizontal_Ri_filter`: Horizontal filter to apply to Ri, which can help alleviate noise for                         some simulations. The default is `nothing`, or no filtering. The other                         option is `horizontal_Ri_filter = FivePointHorizontalFilter()`.
