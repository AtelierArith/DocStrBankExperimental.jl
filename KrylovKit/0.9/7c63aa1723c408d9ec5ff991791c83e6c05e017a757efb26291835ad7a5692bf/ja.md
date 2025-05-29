```
    basis(fact::GKLFactorization, ::Val{which})
```

[`GKLFactorization`](@ref)の基底ベクトルのリストを返します。`which`は`:U`または`:V`の値を取る必要があり、対応する線形写像の定義域またはコドメインのどの基底ベクトルのセットを返すべきかを示します。返り値の型は`OrthonormalBasis{T}`であり、`T`は問題で使用されるベクトルの型を表します。
