PrimitiveWetModelは、湿度を伴う原始方程式のシミュレーションに必要なすべてのモデルコンポーネント（それ自体が構造体）を含んでいます。次のように構築されます。

```
model = PrimitiveWetModel(spectral_grid; kwargs...)
```

`spectral_grid::SpectralGrid`は、キーワード引数として渡されるすべての非デフォルトコンポーネントを初期化するために使用されます。例えば、`planet=Earth(spectral_grid)`のように。モデルコンポーネントを表すフィールドは次のとおりです。

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
