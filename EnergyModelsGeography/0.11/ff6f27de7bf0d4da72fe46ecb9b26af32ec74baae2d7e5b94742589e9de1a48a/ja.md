```
GeoAvailability <: EMB.Availability
```

地理的な `Availability` ノードは、一般的な [`GenAvailability`](@extref EnergyModelsBase.GenAvailability) ノードの置き換え用です。個々の [`Area`](@refs) 間での伝送を含める必要がある場合、`GeoAvailability` が必要です。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`inputs::Vector{<:Resource}`** は入力 [`Resource`](@extref EnergyModelsBase.Resource) です。
  * **`output::Vector{<:Resource}`** は出力 [`Resource`](@extref EnergyModelsBase.Resource) です。
