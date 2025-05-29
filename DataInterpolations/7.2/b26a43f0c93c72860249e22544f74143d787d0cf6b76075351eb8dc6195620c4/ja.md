```
BSplineInterpolation(u, t, d, pVecType, knotVecType; extrapolation::ExtrapolationType.T = ExtrapolationType.None, extrapolation_left::ExtrapolationType.T = ExtrapolationType.None,
    extrapolation_right::ExtrapolationType.T = ExtrapolationType.None)
```

これは、`n` 基底関数の線形結合によって定義される曲線であり、`n` はデータポイントの数です。詳細については、[https://pages.mtu.edu/~shene/COURSES/cs3621/NOTES/spline/B-spline/bspline-curve.html](https://pages.mtu.edu/%7Eshene/COURSES/cs3621/NOTES/spline/B-spline/bspline-curve.html)を参照してください。外挿は、両端の各側の定数多項式です。

## 引数

  * `u`: データポイント。
  * `t`: 時間ポイント。
  * `d`: 区間多項式の次数。
  * `pVecType`: パラメータベクトルのシンボル、均等間隔のパラメータの場合は `:Uniform`、弦長法によって生成されたパラメータの場合は `:ArcLen`。
  * `knotVecType`: ノットベクトルのシンボル、均等ノットベクトルの場合は `:Uniform`、平均間隔のノットベクトルの場合は `:Average`。

## キーワード引数

  * `extrapolation`: データの左側と右側に適用される外挿タイプ。可能なオプションは `ExtrapolationType.None`（デフォルト）、`ExtrapolationType.Constant`、`ExtrapolationType.Linear`、`ExtrapolationType.Extension`、`ExtrapolationType.Periodic`、および `ExtrapolationType.Reflective` です。
  * `extrapolation_left`: データの左側に適用される外挿タイプ。可能なオプションについては `extrapolation` を参照してください。このキーワードは `extrapolation != Extrapolation.none` の場合は無視されます。
  * `extrapolation_right`: データの右側に適用される外挿タイプ。可能なオプションについては `extrapolation` を参照してください。このキーワードは `extrapolation != Extrapolation.none` の場合は無視されます。
  * `assume_linear_t`: 均等に分布したアブシッサに対してより高速なインデックス検索動作を指定するためのブール値。あるいは、直線に対する差の正規化された標準偏差に基づくテストのために数値的しきい値を指定することもできます（[`looks_linear`](@ref)を参照）。デフォルトは 1e-2 です。
