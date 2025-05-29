```
with_vjp_func(f, x, ad::ADSelector)
```

関数 `vjp(z) ≈ J' * z` を持つタプル `(f(x), vjp)` を返します。
