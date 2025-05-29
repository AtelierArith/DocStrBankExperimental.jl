The ShallowWaterModel contains all model components needed for the simulation of the shallow water equations. To be constructed like

```
model = ShallowWaterModel(spectral_grid; kwargs...)
```

with `spectral_grid::SpectralGrid` used to initalize all non-default components passed on as keyword arguments, e.g. `planet=Earth(spectral_grid)`. Fields, representing model components, are

  * `spectral_grid::SpeedyWeather.SpectralGrid`
  * `device_setup::Any`
  * `geometry::Any`
  * `planet::Any`
  * `atmosphere::Any`
  * `coriolis::Any`
  * `orography::Any`
  * `forcing::Any`
  * `drag::Any`
  * `particle_advection::Any`
  * `initial_conditions::Any`
  * `random_process::Any`
  * `tracers::Dict{Symbol, SpeedyWeather.Tracer}`
  * `time_stepping::Any`
  * `spectral_transform::Any`
  * `implicit::Any`
  * `horizontal_diffusion::Any`
  * `output::Any`
  * `callbacks::Dict{Symbol, SpeedyWeather.AbstractCallback}`
  * `feedback::Any`
