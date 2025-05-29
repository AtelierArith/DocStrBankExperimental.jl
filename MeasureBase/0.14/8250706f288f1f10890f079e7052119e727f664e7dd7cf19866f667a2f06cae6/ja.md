```
logdensityof(m::AbstractMeasure, x)
```

測度 `m` の `x` における対数密度を計算します。密度は常に相対的ですが、`DensityInterface.jl` はこれを考慮していません。これとの互換性のために、測度に対する `logdensityof` は常に [`rootmeasure(x)`](@ref rootmeasure) に対して暗黙的に相対的です。

`logdensityof` はまず `insupport(m, x)` を計算することから始まります。これが真であれば、`unsafe_logdensityof` が呼び出されます。`insupport(m, x)` が真であることが知られている場合、`unsafe_logdensityof(m, x)` を直接呼び出す方が少し速くなることがあります。

`basemeasure(m)` に対して相対的な対数密度を計算するか、*定義* する場合は、`logdensity_def` を参照してください。

特定の基準測度に対して相対的な対数密度を計算するには、`logdensity_rel` を参照してください。
