```
sample_predictive(rng, model, θ)
```

モデル `model` の予測分布から `θ` に条件付けてサンプリングします。

# 引数

  * `rng::Random.AbstractRNG`: 擬似乱数生成器。
  * `model`: テスト対象のモデル。
  * `θ`: 条件付けるモデルパラメータ。

# 戻り値

  * `y`: `p(y|θ)` に基づいて `θ` に条件付けて生成されたデータ。
