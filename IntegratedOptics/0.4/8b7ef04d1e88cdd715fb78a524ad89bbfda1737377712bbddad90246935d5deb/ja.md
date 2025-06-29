```
ADAMW(η = 0.001, β::Tuple = (0.9, 0.999), decay = 0)
```

[ADAMW](https://arxiv.org/abs/1711.05101) は、重み減衰正則化を修正する（修理する）ADAMの変種です。

# パラメータ

  * 学習率（`η`）：勾配が重みを更新する前にどれだけ割引かれるかの量。
  * モーメンタムの減衰（`β::Tuple`）：最初の（β1）および2番目の（β2）モーメント推定のための指数的減衰。
  * `decay`：最適化中に重みに適用される減衰。

# 例

```julia
opt = ADAMW()
opt = ADAMW(0.001, (0.89, 0.995), 0.1)
```
