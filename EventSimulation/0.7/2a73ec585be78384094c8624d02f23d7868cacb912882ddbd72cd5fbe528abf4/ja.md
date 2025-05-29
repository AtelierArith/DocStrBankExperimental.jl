```
provide!(s, r, quantity)
provide!(s, q, object)
```

`SimResource`を`quantity`で満たすか、`SimQueue`を`object`で満たすことができます。

`SimResource`では、`r.quantity`の残高が変更されます。与えられたquantityは任意の数値で構いませんが、`SimResource`の残高は`lo`-`hi`の範囲内でのみ変更されます。`SimResource`の残高の実際の変化を返します。

`SimQueue`では、`object`を`q.queue`に追加します。成功した場合は`true`を返し、すでにキューにオブジェクトが多すぎる場合は`false`を返します。
