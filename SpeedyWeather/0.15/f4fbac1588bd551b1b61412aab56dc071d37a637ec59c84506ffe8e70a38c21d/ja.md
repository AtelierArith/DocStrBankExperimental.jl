BarotropicModelは、バロトロピック渦度方程式のシミュレーションに必要なすべてのモデルコンポーネントを含んでいます。次のように構築されます。

```
model = BarotropicModel(spectral_grid; kwargs...)
```

`spectral_grid::SpectralGrid`は、キーワード引数として渡されるすべての非デフォルトコンポーネントを初期化するために使用されます。例えば、`planet=Earth(spectral_grid)`のようにします。モデルコンポーネントを表すフィールドは次のとおりです。

  * `spectral_grid::SpeedyWeather.SpectralGrid`
  * `device_setup::Any`
  * `geometry::Any`
  * `planet::Any`
  * `atmosphere::Any`
  * `coriolis::Any`
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
