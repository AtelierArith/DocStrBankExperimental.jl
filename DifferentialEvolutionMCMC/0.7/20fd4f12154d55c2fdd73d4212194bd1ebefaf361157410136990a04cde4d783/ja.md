```
evaluate_fun!(de, model, proposal))
```

任意の関数 `loglike` の適合度を評価します。これは事前分布を使用しないため、点推定に使用されます。

# 引数

  * `de`: 差分進化オブジェクト
  * `model`: データと事前を含む尤度関数を持つモデル
  * `proposal`: 提案された粒子
