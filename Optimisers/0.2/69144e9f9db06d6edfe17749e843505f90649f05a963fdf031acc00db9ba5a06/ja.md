```
AdaBelief(η = 1f-3, β = (9f-1, 9.99f-1), ϵ = 1e-16)
```

[AdaBelief](https://arxiv.org/abs/2010.07468)オプティマイザは、よく知られたAdamオプティマイザの変種です。

# パラメータ

  * 学習率（`η`）：重みを更新する前に勾配が割引かれる量。
  * モーメンタムの減衰（`β::Tuple`）：最初の（β1）および2番目の（β2）モーメント推定のための指数的減衰。
  * マシンイプシロン（`ϵ::Float32`）：ゼロ除算を防ぐための定数（デフォルトを変更する必要はありません）
