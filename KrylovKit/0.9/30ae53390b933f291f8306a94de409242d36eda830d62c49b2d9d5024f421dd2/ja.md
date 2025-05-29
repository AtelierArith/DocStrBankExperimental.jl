```
rayleighquotient(fact::KrylovFactorization)
```

[`KrylovFactorization`](@ref)のレイリー商を返します。すなわち、クリロフ部分空間の基底内の縮小行列です。返り値の型は`AbstractMatrix{<:Number}`のサブタイプであり、通常は構造化された行列型です。
