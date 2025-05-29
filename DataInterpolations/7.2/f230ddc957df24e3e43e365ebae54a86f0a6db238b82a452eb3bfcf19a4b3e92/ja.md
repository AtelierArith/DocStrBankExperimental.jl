```
QuadraticInterpolation(u, t, mode = :Forward; extrapolation_left::ExtrapolationType.T = ExtrapolationType.None,
    extrapolation::ExtrapolationType.T = ExtrapolationType.None, extrapolation_right::ExtrapolationType.T = ExtrapolationType.None, 
    cache_parameters = false)
```

これは、データポイント間を二次多項式を使用して補間するメソッドです。任意の点について、近くの三つのデータポイントを取り、二次多項式をフィットさせます。外挿は、両側の最後の二次多項式を延長します。

## 引数

  * `u`: データポイント。
  * `t`: 時間ポイント。
  * `mode`: `:Forward` または `:Backward`。`：Forward` の場合、点の前に二つのデータポイント、後ろに一つのデータポイントを取って補間します。`：Backward` の場合、後ろに二つのデータポイント、前に一つのデータポイントを取って補間します。

## キーワード引数

  * `extrapolation`: データの左側と右側に適用される外挿タイプ。可能なオプションは `ExtrapolationType.None`（デフォルト）、`ExtrapolationType.Constant`、`ExtrapolationType.Linear`、`ExtrapolationType.Extension`、`ExtrapolationType.Periodic` および `ExtrapolationType.Reflective` です。
  * `extrapolation_left`: データの左側に適用される外挿タイプ。可能なオプションについては `extrapolation` を参照してください。このキーワードは `extrapolation != Extrapolation.none` の場合は無視されます。
  * `extrapolation_right`: データの右側に適用される外挿タイプ。可能なオプションについては `extrapolation` を参照してください。このキーワードは `extrapolation != Extrapolation.none` の場合は無視されます。
  * `cache_parameters`: より高速な補間計算のために初期化時にパラメータを事前計算します。注意: 有効にした場合、`u` と `t` は変更しないでください。デフォルトは `false` です。
  * `assume_linear_t`: 均等に分布したアブシッサに対してより高速なインデックスルックアップ動作を指定するためのブール値。あるいは、直線に対する差の正規化された標準偏差に基づくテストのために数値的な閾値を指定することもできます（[`looks_linear`](@ref) を参照）。デフォルトは 1e-2 です。
