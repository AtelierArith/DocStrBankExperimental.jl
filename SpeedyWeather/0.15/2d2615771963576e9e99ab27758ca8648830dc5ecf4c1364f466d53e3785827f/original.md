The PrimitiveWetModel contains all model components (themselves structs) needed for the simulation of the primitive equations with humidity. To be constructed like

```
model = PrimitiveWetModel(spectral_grid; kwargs...)
```

with `spectral_grid::SpectralGrid` used to initalize all non-default components passed on as keyword arguments, e.g. `planet=Earth(spectral_grid)`. Fields, representing model components, are

  * `spectral_grid::SpeedyWeather.SpectralGrid`
  * `device_setup::Any`
  * `dynamics::Bool`
  * `geometry::Any`
  * `planet::Any`
  * `atmosphere::Any`
  * `coriolis::Any`
  * `geopotential::Any`
  * `adiabatic_conversion::Any`
  * `particle_advection::Any`
  * `initial_conditions::Any`
  * `forcing::Any`
  * `drag::Any`
  * `random_process::Any`
  * `tracers::Dict{Symbol, SpeedyWeather.Tracer}`
  * `orography::Any`
  * `land_sea_mask::Any`
  * `ocean::Any`
  * `land::Any`
  * `solar_zenith::Any`
  * `albedo::Any`
  * `physics::Bool`
  * `clausius_clapeyron::Any`
  * `boundary_layer_drag::Any`
  * `temperature_relaxation::Any`
  * `vertical_diffusion::Any`
  * `surface_thermodynamics::Any`
  * `surface_wind::Any`
  * `surface_heat_flux::Any`
  * `surface_evaporation::Any`
  * `large_scale_condensation::Any`
  * `convection::Any`
  * `optical_depth::Any`
  * `shortwave_radiation::Any`
  * `longwave_radiation::Any`
  * `stochastic_physics::Any`
  * `time_stepping::Any`
  * `spectral_transform::Any`
  * `implicit::Any`
  * `horizontal_diffusion::Any`
  * `vertical_advection::Any`
  * `hole_filling::Any`
  * `output::Any`
  * `callbacks::Dict{Symbol, SpeedyWeather.AbstractCallback}`
  * `feedback::Any`
