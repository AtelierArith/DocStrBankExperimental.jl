```
map(fn, p::AbstractPolynomial, args...)
```

`p`の係数を変換するために、各係数に関数（または他の呼び出し可能なもの）`fn`を適用します。

`map`を使用して`Polynomial`に`real`などを実装できます。この関数を使用することで、`p`の型が狭まる場合があります。
