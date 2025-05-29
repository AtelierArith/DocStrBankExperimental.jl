```
GRAPE(;max_episode=300, epsilon=0.01, beta1=0.90, beta2=0.99, Adam::Bool=true)
```

制御最適化アルゴリズム: GRAPE。

  * `max_episode`: エピソードの数。
  * `epsilon`: 学習率。
  * `beta1`: 最初のモーメント推定の指数減衰率。
  * `beta2`: 第二のモーメント推定の指数減衰率。
  * `Adam`: 制御係数を更新するためにAdamを使用するかどうか。
