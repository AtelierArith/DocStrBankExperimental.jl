```
ShallowUnitaryMeasurementSetting(N, depth; site_indices=nothing)
```

ランダム量子回路を生成することによって `ShallowUnitaryMeasurementSetting` オブジェクトを作成します。

# 引数:

  * `N::Int`: サイト数（キュービット）。
  * `depth::Int`: ランダム回路の深さ。
  * `site_indices::Union{Vector{Index{Int64}}, Nothing}`（オプション）: サイトインデックス。`nothing` の場合、自動的に生成されます。

# 戻り値:

  * `ShallowUnitaryMeasurementSetting` オブジェクト。

# 例:

```julia
setting = ShallowUnitaryMeasurementSetting(4, 3)
```
