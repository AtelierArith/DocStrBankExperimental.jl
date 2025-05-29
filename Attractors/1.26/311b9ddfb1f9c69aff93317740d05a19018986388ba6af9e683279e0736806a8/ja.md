```
stability_measures_along_continuation(
    ds::DynamicalSystem, attractors_cont, pcurve, ics;
    kw...
)
```

以前の[`global_continuation`](@ref)の呼び出しで見つかったアトラクターを使用して、[`StabilityMeasuresAccumulator`](@ref)によって推定されたすべての安定性測度のグローバル継続を実行します。

このメソッドは特別で、グローバル継続の特定の点でアトラクターのために常に[`AttractorsViaProximity`](@ref)マッパーを作成し、その後、[`StabilityMeasuresAccumulator`](@ref)と近接マッパーを使用して安定性測度を推定します。実際には、収束時間に関連する測度に興味がある場合にのみ、このメソッドを使用することをお勧めします。収束時間はより厳密に定義され、近接マッパーに対してより正確に推定されます。

## キーワード引数

キーワード`ε, finite_time, weighting_distribution`は、異なる継続ステップに対して異なる値を提供するために、`pcurve`と同じ長さの`Vector`であることが許可されています。

  * `ε = nothing`: [`AttractorsViaProximity`](@ref)に渡されます。
  * `proximity_mapper_options = NamedTuple()`: `AttractorsViaProximity`のための追加のキーワード。
  * `metric, finite_time, weighting_distribution`: [`StabilityMeasuresAccumulator`](@ref)に渡されます。
  * `samples_per_parameter = 1000`: [`StabilityMeasuresAccumulator`](@ref)を介して安定性測度を推定する際に使用するサンプル数。`ics`が関数でない場合は無視されます。
