```
with_vjp_func(f, x, ad::ADSelector)
```

Returns a tuple `(f(x), vjp)` with the function `vjp(z) ≈ J' * z`.
