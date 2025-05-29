```
with_gradient(f, x, ad::ADSelector)
```

`f`の`x`における勾配∇f(x)を持つタプル(f(x), ∇f(x))を返します。

この関数の「おそらくインプレース」バリアントについては、[`with_gradient!!(f, δx, x, ad)`](@ref)も参照してください。
