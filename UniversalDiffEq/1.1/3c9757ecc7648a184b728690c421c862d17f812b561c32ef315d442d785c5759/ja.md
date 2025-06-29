```
 SGLD!(UDE, kwargs ...)
```

UDEのパラメータに対してベイズ推定を行うために、確率的勾配ランジュバン動力学（SGLD）サンプリングアルゴリズムを使用します。各ステップ`t`で、確率的更新は平均0のランダム変数εとノイズηによって提供されます。

`math  ϵ = a*(b + t-1)^-γ`

# kwargs

  * `a`: デフォルトは`10.0`。
  * `b`: デフォルトは`1000`。
  * `γ`: デフォルトは0.9。
  * `samples`: サンプリングされるパラメータの数。デフォルトは`500`。
  * `burnin`: ベイズアルゴリズムのバーニングインに使用されるサンプルの数。デフォルトは`samples/10`。
  * `verbose`: トレーニング損失値を印刷するべきか？デフォルトは`true`。

```
