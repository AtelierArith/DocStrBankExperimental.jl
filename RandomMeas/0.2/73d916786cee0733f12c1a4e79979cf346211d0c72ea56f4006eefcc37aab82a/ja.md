```
ComputationalBasisMeasurementSetting(N; site_indices=nothing)
```

`N`サイトのための`ComputationalBasisMeasurementSetting`を作成します。この設定は計算基底での測定に対応します。

# 引数:

  * `N::Int`: サイトの数（キュービット）。
  * `site_indices::Union{Vector{Index{Int64}}, Nothing}`（オプション）: サイトのインデックス。`nothing`の場合、自動的に生成されます。

# 戻り値:

  * `ComputationalBasisMeasurementSetting`オブジェクト。

# 例:

```julia
setting = ComputationalBasisMeasurementSetting(4)
```
