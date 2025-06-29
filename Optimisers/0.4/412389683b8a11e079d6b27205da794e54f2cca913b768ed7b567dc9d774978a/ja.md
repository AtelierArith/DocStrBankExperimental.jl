```
OAdam(η = 0.001, β = (0.5, 0.9), ϵ = 1e-8)
OAdam(; [eta, beta, epsilon])
```

[OAdam](https://arxiv.org/abs/1711.00141) (楽観的Adam) は、敵対的トレーニングに適した「楽観的」項を追加したAdamの変種です。

# パラメータ

  * 学習率 (`η == eta`): 勾配が重みを更新する前に割引かれる量。
  * モーメンタムの減衰 (`β::Tuple == beta`): 最初の (β1) および第二の (β2) モーメント推定の指数的減衰。
  * マシンイプシロン (`ϵ == epsilon`): ゼロ除算を防ぐための定数 (デフォルトを変更する必要はありません)
