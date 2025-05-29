```
 gradient_descent!(UDE, kwargs ...)
```

`UDE`モデルの損失関数を、ステップサイズ`step_size`と最大反復回数`maxiter`を用いて勾配降下法で最小化します。`maxiter`がtrueのとき、各反復後に損失関数の値を印刷します。

# kwargs

  * `step_size`: ADAMオプティマイザのステップサイズ。デフォルトは`0.05`です。
  * `maxiter`: 勾配降下法の最大反復回数。デフォルトは`500`です。
  * `verbose`: トレーニング損失値を印刷するべきですか？デフォルトは`false`です。

```
