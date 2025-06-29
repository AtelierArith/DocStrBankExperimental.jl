```
TKEDissipationVerticalDiffusivity([time_discretization = VerticallyImplicitTimeDiscretization(),
                                  FT = Float64;]
                                  tke_dissipation_equations = TKEDissipationEquations(),
                                  stability_functions = VariableStabilityFunctions(),
                                  minimum_length_scale = StratifiedDisplacementScale(),
                                  maximum_tracer_diffusivity = Inf,
                                  maximum_tke_diffusivity = Inf,
                                  maximum_dissipation_diffusivity = Inf,
                                  maximum_viscosity = Inf,
                                  minimum_tke = 1e-6,
                                  minimum_stratification_number_safety_factor = 0.73,
                                  negative_tke_damping_time_scale = 1minute,
                                  tke_dissipation_time_step = nothing)
```

Return the `TKEDissipationVerticalDiffusivity` turbulence closure for vertical mixing by microscale ocean turbulence based on the prognostic evolution of two variables: the turbulent kinetic energy (TKE), and the turbulent kinetic energy dissipation. Elsewhere this is referred to as "k-ϵ". For more information about k-ϵ, see Burchard and Bolding (2001), Umlauf and Buchard (2003), and Umlauf and Burchard (2005).

# Arguments

  * `time_discretization`: Either `ExplicitTimeDiscretization()` or `VerticallyImplicitTimeDiscretization()`;                        default `VerticallyImplicitTimeDiscretization()`.
  * `FT`: Float type; default `Float64`.

# Keyword arguments

  * `maximum_diffusivity`: Maximum value for tracer, momentum, and TKE diffusivities.                        Used to clip the diffusivity when/if                        TKEDissipationVerticalDiffusivity predicts diffusivities                        that are too large.                        Default: `Inf`.
  * `minimum_tke`: Minimum value for the turbulent kinetic energy.                Can be used to model the presence "background" TKE                levels due to, for example, mixing by breaking internal waves.                Default: 1e-9.
  * `negative_tke_damping_time_scale`: Damping time-scale for spurious negative values of TKE,                                    typically generated by oscillatory errors associated                                    with TKE advection.                                    Default: 1 minute.

Note that for numerical stability, it is recommended to either have a relative short `negative_turbulent_kinetic_energy_damping_time_scale` or a reasonable `minimum_turbulent_kinetic_energy`, or both.
