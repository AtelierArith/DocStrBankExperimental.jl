```
mcd(data; alpha = 0.01)
```

ロバスト共分散行列のための最小共分散決定アルゴリズムを実行します。

# 引数

  * `data::DataFrame`: 多変量データ。
  * `alpha::Float64`: カイ二乗統計量の分位数の確率。

# 説明

`mcd`はロバストな位置ベクトルとロバストなスケール行列（例えば共分散行列）を探索します。このメソッドは、ロバストな対になる代わりに平均ベクトルと通常の共分散行列を使用して計算されるマハラノビス距離という使用可能な診断測定値も報告します。マハラノビス距離は、`p`自由度のカイ二乗分布の分位数と直接比較可能です。

# 出力

  * `["goal"]`: 目的値
  * `["best.subset"]`: 観測の最良h部分集合のインデックス
  * `["robust.location"]`: ロバストな位置測定のベクトル
  * `["robust.covariance"]`: ロバストな共分散行列
  * `["squared.mahalanobis"]`: ロバストな位置とスケール測定を使用して計算されたマハラノビス距離の配列。
  * `["chisq.crit"]`: 閾値で使用されるカイ二乗分位数
  * `["alpha"]`: カイ二乗分位数を計算する際に使用される確率、例えば`chisq.crit`
  * `["outliers"]`: 外れ値のインデックスの配列。

# 注意事項

アルゴリズムは、参考文献に記載されている集中ステップを使用して実装されています。ただし、反復回数に関する詳細は若干異なります。

# 参考文献

Rousseeuw, Peter J., and Katrien Van Driessen. "A fast algorithm for the minimum covariance  determinant estimator." Technometrics 41.3 (1999): 212-223.
