```
LocalUnitaryMeasurementSetting(N, local_unitary, site_indices)
```

各量子ビットが単一量子ビット回転によって指定される測定設定。計算基底から測定基底への回転を行います。

# フィールド

  * `N::Int`: サイト数（量子ビット）。
  * `local_unitary::Vector{ITensor}`: ローカルユニタリ基底回転を表す長さ `N` の ITensor のベクトル。
  * `site_indices::Vector{Index{Int64}}`: 長さ `N` のサイトインデックスのベクトル。

# 制約

  * `N == length(local_unitary) == length(site_indices)`。
  * `local_unitary` の各 ITensor は正確に **2つのインデックス** を持つ：

      * 1つの非プライム（`site_indices[i]`）
      * 1つのプライム（`prime(site_indices[i])`）。
