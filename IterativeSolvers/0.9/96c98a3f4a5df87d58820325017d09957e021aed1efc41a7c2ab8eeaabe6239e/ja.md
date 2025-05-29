```
invpowm!(B, x0; shift = σ, kwargs...) -> λ, x, [history]
```

`shift`の近くにある行列$A$の近似固有対`(λ, x)`を見つけます。ここで、`B`は線形写像であり、`B * v = inv(A - σI) * v`の効果があります。

このメソッドは`powm!(B, x0; inverse = true, shift = σ)`を呼び出します。[`powm!`](@ref)を参照してください。
