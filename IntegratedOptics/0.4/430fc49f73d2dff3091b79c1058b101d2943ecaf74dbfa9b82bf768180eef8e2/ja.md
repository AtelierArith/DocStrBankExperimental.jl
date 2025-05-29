```
NADAM(η = 0.001, β::Tuple = (0.9, 0.999))
```

[NADAM](https://openreview.net/forum?id=OM0jvwB8jIp57ZJjtNEZ) は ADAM のネステロフバリアントです。パラメータの調整は必要ありません。

# パラメータ

  * 学習率 (`η`): 勾配が重みを更新する前に割引かれる量。
  * モーメンタムの減衰 (`β::Tuple`): 最初の (β1) および二番目の (β2) モーメンタム推定の指数的減衰。

# 例

```julia
opt = NADAM()
opt = NADAM(0.002, (0.89, 0.995))
```
