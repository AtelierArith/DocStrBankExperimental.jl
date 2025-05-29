```
init_sigma(rng, error; init_dist)
```

エラーモデルに基づいてσパラメータを初期化する関数。

# 引数

  * `rng::AbstractRNG`: 使用するランダマイザー。
  * `error`: エラーモデル。AdditiveError、ProportionalError、CombinedError、またはCustomErrorのいずれか。
  * `init_dist::Sampleable`: 初期σをサンプリングするための分布。デフォルト = Uniform(0, 1)
