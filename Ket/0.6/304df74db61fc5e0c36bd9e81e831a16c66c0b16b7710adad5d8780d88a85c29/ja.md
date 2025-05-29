```
tensor_probability(FC::Matrix, behaviour::Bool = false)
```

二部ベル関数 `FC` を相関表記から確率表記に変換します。`behaviour` が `true` の場合は、代わりに行動の変換を行います。正規化は仮定しません。
