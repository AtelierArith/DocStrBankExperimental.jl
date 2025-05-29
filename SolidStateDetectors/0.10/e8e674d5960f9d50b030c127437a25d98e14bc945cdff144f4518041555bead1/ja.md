```
Grid(sim::Simulation{T, Cartesian}; kwargs...)
Grid(sim::Simulation{T, Cylindrical}; kwargs...)
```

[`Grid`](@ref)を[`Simulation`](@ref)で定義されたオブジェクトに基づいて初期化します。

すべてのオブジェクトの重要なポイントがサンプリングされ、グリッドのティックに追加されます。グリッドの初期化は、以下にリストされたキーワード引数のセットを使用して調整できます。

## 引数

  * `sim::Simulation{T, S}`: グリッドが定義される[`Simulation`](@ref)。

## キーワード

  * `max_tick_distance = missing`: グリッドの隣接するティック間の最大距離。隣接するティックが遠すぎる場合、追加のグリッドティックが追加されます。`max_tick_distance`は`Quantity`、例えば`1u"mm"`、または`Quantity`のタプル、例えば`(1u"mm", 15u"°", 3u"mm")`として設定でき、`Grid`の各軸に対して個別に設定できます。`CartesianGrid3D`は`Tuple{LengthQuantity, LengthQuantity, LengthQuantity}`を必要とし、`CylindricalGrid`は`Tuple{LengthQuantity, AngleQuantity, LengthQuantity}`を必要とします。`max_tick_distance`が`missing`の場合、軸の長さの4分の1が使用されます。
  * `max_distance_ratio::Real = 5`: ティックとその左および右の隣接ティックとの比率が`max_distance_ratio`を超える場合、さらに離れたティックの間に追加のティックが追加されます。これにより、ティックが不均等に間隔を空けられるのを防ぎます。
  * `add_ticks_between_important_ticks::Bool = true`: `true`に設定すると、シミュレーションのオブジェクトからサンプリングされた重要なポイントの間に追加のポイントが追加されます。オブジェクトが近すぎる場合、ポテンシャルやフィールドの計算においてそれらの間に目立つギャップが確保されます。
  * `for_weighting_potential::Bool = false`: `true`に設定すると、[`ElectricPotential`](@ref)の計算のためにグリッドが最適化され、`false`に設定すると[`WeightingPotential`](@ref)のために最適化されます。
