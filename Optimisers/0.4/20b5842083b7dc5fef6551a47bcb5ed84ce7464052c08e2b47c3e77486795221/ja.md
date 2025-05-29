```
AdaGrad(η = 0.1, ϵ = 1e-8)
AdaGrad(; [eta, epsilon])
```

[AdaGrad](http://www.jmlr.org/papers/volume12/duchi11a/duchi11a.pdf) オプティマイザ。更新頻度に基づいて特定の学習率を持つパラメータがあります。パラメータの調整は必要ありません。

# パラメータ

  * 学習率 (`η == eta`): 勾配が重みを更新する前に割引かれる量。
  * マシンイプシロン (`ϵ == epsilon`): ゼロ除算を防ぐための定数（デフォルトを変更する必要はありません）
