```
AdaGrad(η = 1f-1, ϵ = eps(typeof(η)))
```

[AdaGrad](http://www.jmlr.org/papers/volume12/duchi11a/duchi11a.pdf) オプティマイザ。更新頻度に基づいて特定の学習率を持つパラメータです。パラメータの調整は必要ありません。

# パラメータ

  * 学習率 (`η`): 勾配が重みを更新する前にどれだけ割引かれるかの量。
  * マシンイプシロン (`ϵ`): ゼロ除算を防ぐための定数（デフォルトを変更する必要はありません）
