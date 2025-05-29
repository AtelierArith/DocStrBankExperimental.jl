```
gram_operate(::typeof(+), p::GramMatrix, q::GramMatrix)
```

`p` と `q` の和に等しいグラム行列を計算します。逆に、`p + q` は `p + q` に等しい多項式を返します。多項式 `p + q` は `polynomial(gram_operate(+, p, q))` を使っても得ることができます。
