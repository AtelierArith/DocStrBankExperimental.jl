```
printWeightsBiases(net, nn_params; print_values = false)
```

ニューラルネットワークのすべての重みとバイアスを出力します。

# 引数:

  * `net`: 抽象レイヤー名を取得するためのニューラルネットワークモデル
  * `nn_params`: ニューラルネットワークのパラメータ
  * `print_values`: `true` の場合、重みとバイアスの値を出力します。デフォルトは `false` で、形状のみを出力します。
