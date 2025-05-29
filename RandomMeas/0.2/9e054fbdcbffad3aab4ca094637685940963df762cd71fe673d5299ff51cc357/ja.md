```
MeasurementData{T}
```

実際のまたはシミュレーションされた量子実験で得られた測定データと設定のコンテナです。

# フィールド

  * `N::Int`: サイト数（キュービット）。
  * `NM::Int`: 設定ごとの測定数。
  * `measurement_results::Array{Int, 2}`: 次元が `(NM, N)` のバイナリ測定結果の2D配列。
  * `measurement_setting::T`: タイプ `T`（`AbstractMeasurementSetting` のサブタイプ）または `nothing` の測定設定。

# 型パラメータ

  * `T`: 測定設定の型で、`Union{Nothing, AbstractMeasurementSetting}` に制約されています。

# 使用法

通常は提供されたコンストラクタを介して構築されます。
