```
AkimaInterpolation(u, t; extrapolation::ExtrapolationType.T = ExtrapolationType.None, extrapolation_left::ExtrapolationType.T = ExtrapolationType.None,
    extrapolation_right::ExtrapolationType.T = ExtrapolationType.None, cache_parameters = false)
```

これは三次多項式から構築されたスプライン補間です。連続的に微分可能な関数を形成します。詳細については、[https://en.wikipedia.org/wiki/Akima_spline](https://en.wikipedia.org/wiki/Akima_spline)を参照してください。外挿は、両側の最後の三次多項式を延長します。

## 引数

  * `u`: データポイント。
  * `t`: 時間ポイント。

## キーワード引数

  * `extrapolation`: データの左側と右側に適用される外挿タイプ。可能なオプションは、`ExtrapolationType.None`（デフォルト）、`ExtrapolationType.Constant`、`ExtrapolationType.Linear`、`ExtrapolationType.Extension`、`ExtrapolationType.Periodic`、および`ExtrapolationType.Reflective`です。
  * `extrapolation_left`: データの左側に適用される外挿タイプ。可能なオプションについては`extrapolation`を参照してください。このキーワードは、`extrapolation != Extrapolation.none`の場合は無視されます。
  * `extrapolation_right`: データの右側に適用される外挿タイプ。可能なオプションについては`extrapolation`を参照してください。このキーワードは、`extrapolation != Extrapolation.none`の場合は無視されます。
  * `cache_parameters`: より高速な補間計算のために初期化時にパラメータを事前計算します。注意: 有効にした場合、`u`と`t`は変更しないでください。デフォルトは`false`です。
  * `assume_linear_t`: 均等に分布したアブシッサに対してより高速なインデックスルックアップ動作を指定するためのブール値。あるいは、直線に対する差の正規化された標準偏差に基づくテストのために数値的な閾値を指定することもできます（[`looks_linear`](@ref）を参照）。デフォルトは1e-2です。

```
