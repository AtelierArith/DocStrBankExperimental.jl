```
    basis(fact::KrylovFactorization)
```

[`KrylovFactorization`](@ref) の基底ベクトルのリストを返します。これらはクライロフ部分空間を張ります。返される型は `Basis{T}` のサブタイプであり、ここで `T` は問題で使用されるベクトルの型を表します。
