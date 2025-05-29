```
normres(fact::KrylovFactorization)
```

[`KrylovFactorization`](@ref) の残差のノルムを返します。これは通常すでに計算されているため、`norm(residual(F))` よりも安価ですが、それ以外は同等です。
