```
mutable struct Stage{L <: LifeStage}
    μ_temperature_response::TemperatureResponse
    q_temperature_response::TemperatureResponse
    n::Union{Nothing, Int64}
    density::Density{<: DensityDependence}
    dependency::Union{Nothing, Type{<:LifeStage}}
    N0::Int64
end
```

ライフステージのデータ。ステージ構造の個体群方程式で表される任意の生物に適用されます。

# 引数

  * `μ_temperature_response::TemperatureResponse`: 死亡率。温度に応じて変化します。
  * `q_temperature_response::TemperatureResponse`: 発達率。ステージで過ごす総時間（日数またはその一部）の逆数。温度に応じて変化します。
  * `n::Union{Nothing, Int64}`: ステージに割り当てられたビンの数（パラメータ、エルラン分布）。
  * `density::Density`: 密度依存モデルを指定します。
  * `dependency::Union{Nothing, Type{<:LifeStage}}`: 生物内部の参照、変更しないでください。
  * `N0::Int64`: ノードごとの初期ステージ特有の個体数。`Female`ライフステージ以外のすべてのステージには「0」を指定してください。
