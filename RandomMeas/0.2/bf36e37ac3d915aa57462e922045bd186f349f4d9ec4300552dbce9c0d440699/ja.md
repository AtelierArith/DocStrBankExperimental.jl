```
ComputationalBasisMeasurementSetting
```

量子システムの計算基準測定設定を表す構造体。この設定は計算基準を使用しているため、各ローカルユニタリは構造的に単に単位演算子です。

# フィールド

  * `N::Int`: サイト数（キュービット）。
  * `local_unitary::Vector{ITensor}`: N 個の単位 ITensor のベクトル。
  * `site_indices::Vector{Index{Int64}}`: サイトインデックスのベクトル（長さ N）。

# 制約

  * `N == length(site_indices)`。
