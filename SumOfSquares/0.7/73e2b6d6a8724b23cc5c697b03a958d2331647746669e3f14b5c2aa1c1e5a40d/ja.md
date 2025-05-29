```
gram_operate(/, p::GramMatrix, α)
```

`p / α` に等しいグラム行列を計算します。逆に、`p / α` は `p / α` に等しい多項式を返します。多項式 `p / α` は `polynomial(gram_operate(/, p, α))` によっても得られます。
