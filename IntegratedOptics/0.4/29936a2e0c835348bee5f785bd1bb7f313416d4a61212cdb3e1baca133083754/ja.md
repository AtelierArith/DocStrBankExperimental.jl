```
ADAGrad(η = 0.1)
```

[ADAGrad](http://www.jmlr.org/papers/volume12/duchi11a/duchi11a.pdf) オプティマイザ。更新頻度に基づいて特定の学習率を持つパラメータがあります。パラメータの調整は必要ありません。

# パラメータ

  * 学習率 (`η`): 勾配が重みを更新する前に割引かれる量。

# 例

```julia
opt = ADAGrad()
opt = ADAGrad(0.001)
```
