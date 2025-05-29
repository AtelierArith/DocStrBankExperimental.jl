```
bic(max_loglike, k, n)
```

ベイズ情報基準 (BIC) を計算します。

# 引数

  * `max_loglike`: 最大尤度推定値で評価された対数尤度
  * `k`: モデルのパラメータの数
  * `n`: データの観測数

# 戻り値

  * `bic::Real`: BIC 値
