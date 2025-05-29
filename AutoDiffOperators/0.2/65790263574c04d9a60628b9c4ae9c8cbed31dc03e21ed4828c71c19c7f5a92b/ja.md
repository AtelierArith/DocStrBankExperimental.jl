```
valgrad_func(f, ad::ADSelector)
```

指定された点での `f` の値と勾配を計算する関数 `f_∇f` を返します。したがって、`f_∇f(x)` は [`with_gradient(f, x, ad)`](@ref) と同等です。
