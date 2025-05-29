kolmogorov*smirnov*test

与えられたデータと分布に対して[コルモゴロフ・スミルノフ検定](https://www.encyclopediaofmath.org/index.php/Kolmogorov-Smirnov_test)を計算します。

# 引数

  * `dat::AbstractArray`: 検定されるデータ。
  * `d::UnivariateDistribution`: 検定される分布（`ContinuousPowerLaw`または`DiscretePowerLaw`）。
  * `xmin::Number`: 考慮されるデータの最小値。
  * `xmax::Int64`: 考慮されるデータの最大値。デフォルトは`1e5`です。

# 戻り値

  * `KS::Float64`: データと分布の間のコルモゴロフ・スミルノフ距離。これは、経験的および理論的累積分布関数（`cdf`）の間の最大絶対差です。
