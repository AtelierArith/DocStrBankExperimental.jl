```
ConstantInterpolation(u, t; dir = :left, extrapolation::ExtrapolationType.T = ExtrapolationType.None, extrapolation_left::ExtrapolationType.T = ExtrapolationType.None,
    extrapolation_right::ExtrapolationType.T = ExtrapolationType.None, cache_parameters = false)
```

これは定数多項式を使用して補間するメソッドです。任意の点に対して、左右の隣接データポイントが見つかります。値は `dir` に依存します。`:left` の場合は左の点の値が選ばれ、`:right` の場合は右の点の値が選ばれます。外挿は、各側の端点で最後の定数多項式を延長します。

## 引数

  * `u`: データポイント。
  * `t`: 時間ポイント。

## キーワード引数

  * `dir`: 補間に使用する値を示します（`:left` または `:right`）。
  * `extrapolation`: データの左側と右側に適用される外挿タイプ。可能なオプションは `ExtrapolationType.None`（デフォルト）、`ExtrapolationType.Constant`、`ExtrapolationType.Linear`、`ExtrapolationType.Extension`、`ExtrapolationType.Periodic`、および `ExtrapolationType.Reflective` です。
  * `extrapolation_left`: データの左側に適用される外挿タイプ。可能なオプションについては `extrapolation` を参照してください。このキーワードは `extrapolation != Extrapolation.none` の場合は無視されます。
  * `extrapolation_right`: データの右側に適用される外挿タイプ。可能なオプションについては `extrapolation` を参照してください。このキーワードは `extrapolation != Extrapolation.none` の場合は無視されます。
  * `cache_parameters`: 初期化時にパラメータを事前計算して、補間計算を高速化します。注意: 有効にした場合、`u` と `t` は変更しないでください。デフォルトは `false` です。
  * `assume_linear_t`: 均等に分布したアブシッサに対して、より高速なインデックスルックアップ動作を指定するブール値。あるいは、直線に対する差の正規化標準偏差に基づくテストのために数値しきい値を指定することもできます（[`looks_linear`](@ref) を参照）。デフォルトは 1e-2 です。

```
