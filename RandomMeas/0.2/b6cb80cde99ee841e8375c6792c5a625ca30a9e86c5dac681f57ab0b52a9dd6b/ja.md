```
LocalUnitaryMeasurementSetting(local_unitary_array; site_indices=nothing)
```

`N × 2 × 2` のユニタリ行列の配列から `LocalUnitaryMeasurementSetting` オブジェクトを作成します。

# 引数:

  * `local_unitary_array::Array{ComplexF64, 3}`: `N × 2 × 2` のユニタリ行列の配列。
  * `site_indices::Union{Vector{Index{Int64}}, Nothing}` (オプション): サイトインデックス。`nothing` の場合、自動的に生成されます。

# 戻り値:

  * `LocalUnitaryMeasurementSetting` オブジェクト。

# 例:

```julia
unitary_array = rand(ComplexF64, 4, 2, 2)
setting = LocalUnitaryMeasurementSetting(unitary_array)
```
