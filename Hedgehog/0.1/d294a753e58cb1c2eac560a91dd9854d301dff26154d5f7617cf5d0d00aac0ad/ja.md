```
parity_transform(call_price, opt::VanillaOption{T, E, Put, U}, spot, rate_curve)
```

既知のコール価格からプット価格を回復するためにプット・コール・パリティを適用します。

# 引数

  * `call_price`: コールオプションの価格。
  * `opt`: `Put()`ペイオフを持つ`VanillaOption`。
  * `spot`: 現物価格。
  * `rate_curve`: 金利曲線。

# 戻り値

  * `put = call - S + K * exp(-rT)`という式を使用して対応するプット価格を返します。ここで、`T`は`opt.expiry`から抽出されます。
