```
LocalUnitaryMeasurementSetting(N; site_indices=nothing, ensemble="Haar")
```

ローカルユニタリ測定設定オブジェクトを、ローカルユニタリ演算子をランダムにサンプリングすることで作成します。

# 引数:

  * `N::Int`: サイト数（キュービット）。
  * `site_indices::Union{Vector{Index}, Nothing}`（オプション）: サイトインデックス。`nothing`の場合、自動的に生成されます。
  * `ensemble::String`: ランダムユニタリのタイプ（`"Haar"`、`"Pauli"`、`"Identity"`）。

# 戻り値:

  * `LocalUnitaryMeasurementSetting`オブジェクト。

# 例:

```julia
setting = LocalUnitaryMeasurementSetting(4, ensemble="Haar")
```
