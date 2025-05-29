```
T2{tp}(data::AbstractArray{tp,2}, Q::AbstractArray[, mv])
```

ホテリングの T2 管理図を計算します（データの平均ベクトル（`mv`）に対する二乗マハラノビス距離、共分散行列 `Q` が与えられます）。入力データは二次元データ行列（観測 * 変数）です。

Lowry, C. A., & Woodall, W. H. (1992). A Multivariate Exponentially Weighted Moving Average Control Chart. Technometrics, 34, 46–53.
