```
MeasurementProbability{T}

測定データから推定されたか、量子状態から直接計算された測定確率と設定のコンテナです。
```

# フィールド

  * `N::Int`: サイト数（キュービット）。
  * `measurement_probability::ITensor`: ボルン確率を表すITensor。
  * `measurement_setting::T`: 型 `T` の測定設定または `nothing`。
  * `site_indices::Vector{Index{Int64}}`: サイトインデックスのベクター（長さ N）。

# 型パラメータ

  * `T`: 測定設定の型で、`Union{Nothing, AbstractMeasurementSetting}` に制約されています。

# 使用法

測定データからまたは量子状態から直接構築されます。
