```
CATKEVerticalDiffusivity([time_discretization = VerticallyImplicitTimeDiscretization(),
                         FT = Float64;]
                         mixing_length = CATKEMixingLength(),
                         turbulent_kinetic_energy_equation = CATKEEquation(),
                         maximum_tracer_diffusivity = Inf,
                         maximum_tke_diffusivity = Inf,
                         maximum_viscosity = Inf,
                         minimum_tke = 1e-9,
                         minimum_convective_buoyancy_flux = 1e-11,
                         negative_tke_damping_time_scale = 1minute,
                         tke_time_step = nothing)
```

Return the `CATKEVerticalDiffusivity` turbulence closure for vertical mixing by small-scale ocean turbulence based on the prognostic evolution of subgrid Turbulent Kinetic Energy (TKE).

!!! note "CATKE vertical diffusivity"
    `CATKEVerticalDiffusivity` is a new turbulence closure diffusivity. The default values for its free parameters are obtained from calibration against large eddy simulations. For more details please refer to [Wagner25catke](@cite).

    Use with caution and report any issues with the physics at https://github.com/CliMA/Oceananigans.jl/issues.


# Arguments

  * `time_discretization`: Either `ExplicitTimeDiscretization()` or `VerticallyImplicitTimeDiscretization()`;                        default `VerticallyImplicitTimeDiscretization()`.
  * `FT`: Float type; default `Float64`.

# Keyword arguments

  * `mixing_length`: The formulation for mixing length; default: `CATKEMixingLength()`.
  * `turbulent_kinetic_energy_equation`: The TKE equation; default: `CATKEEquation()`.
  * `maximum_tracer_diffusivity`: Maximum value for tracer diffusivity. CATKE-predicted tracer diffusivities that are larger                               than `maximum_tracer_diffusivity` are clipped. Default: `Inf`.
  * `maximum_tke_diffusivity`: Maximum value for TKE diffusivity. CATKE-predicted diffusivities for TKE that are larger                            than `maximum_tke_diffusivity` are clipped. Default: `Inf`.
  * `maximum_viscosity`: Maximum value for momentum diffusivity. CATKE-predicted momentum diffusivities that are larger                      than `maximum_viscosity` are clipped. Default: `Inf`.
  * `minimum_tke`: Minimum value for the turbulent kinetic energy.                Can be used to model the presence "background" TKE                levels due to, for example, mixing by breaking internal waves.                Default: 1e-9.
  * `minimum_convective_buoyancy_flux` Minimum value for the convective buoyancy flux. Default: 1e-11.
  * `negative_tke_damping_time_scale`: Damping time-scale for spurious negative values of TKE,                                    typically generated by oscillatory errors associated                                    with the TKE advection. Default: 1 minute.

# References

Wagner, G. L., Hillier, A., Constantinou, N. C., Silvestri, S., Souza, A., Burns, K., Hill,     C., Campin, J.-M., Marshall, J., and Ferrari, R. (2025). "Formulation and calibration of CATKE,     a one-equation parameterization for microscale ocean mixing." J. Adv. Model. Earth Sy., 17, e2024MS004522.
