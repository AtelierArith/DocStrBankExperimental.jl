```
compute_posterior!(de, model, proposal)
```

提案された粒子の事後対数尤度を計算します。提案が範囲外の場合は、-Inf が返されます。

# 引数

  * `de`: 差分進化オブジェクト
  * `model`: データと事前を含む尤度関数を持つモデル
  * `proposal`: 提案された粒子
