```
parity_transform(call_price, opt::VanillaOption{T, E, Call, U}, spot, rate_curve)
```

コール価格を変更せずに返します。コールとプットの両方を受け入れる統一された価格設定APIに便利です。

# 引数

  * `call_price`: コールオプションの価格。
  * `opt`: `Call()`ペイオフを持つ`VanillaOption`。
  * `spot`: 現物価格。
  * `rate_curve`: 金利曲線。

# 戻り値

  * 同じ`call_price`、変更なし。
