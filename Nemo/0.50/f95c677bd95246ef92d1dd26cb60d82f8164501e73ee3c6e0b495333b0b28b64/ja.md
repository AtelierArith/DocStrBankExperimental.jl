```
pow(a::CalciumFieldElem, b::Int; form::Symbol=:default)
```

整数の冪 `b` で *a* を累乗します。オプションの `form` 引数は表現を指定することを可能にします。`:default` 形式では、これは `a ^ b` と同等であり、指数 `b` が大きすぎる場合（親オプション `:pow_limit` またはケースに応じて `:prec_limit` によって決定される）には新しい拡張数 $a^b$ を作成することがあります。`:arithmetic` 形式では、累乗は指数 `b` の大きさに関係なく、`a` の体内で算術的に行われます。
