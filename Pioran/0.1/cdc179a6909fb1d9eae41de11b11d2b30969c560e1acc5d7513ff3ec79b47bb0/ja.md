```
log_likelihood(cov, τ, y, σ2)
```

セミセパラブル共分散関数の対数尤度をceleriteアルゴリズムを使用して計算します。

# 引数

  * `cov::SumOfSemiSeparable` または `cov::CARMA` または `cov::SemiSeparable`: 共分散関数
  * `τ::Vector`: 時間点
  * `y::Vector`: データ
  * `σ2::Vector`: 測定分散
