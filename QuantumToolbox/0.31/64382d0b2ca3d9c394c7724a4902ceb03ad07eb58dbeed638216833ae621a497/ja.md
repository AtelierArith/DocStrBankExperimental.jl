```
tunneling(N::Int, m::Int=1; sparse::Union{Bool,Val{<:Bool}}=Val(false))
```

トンネリング演算子を次のように定義します：

$$
\sum_{n=0}^{N-m} | n \rangle\langle n+m | + | n+m \rangle\langle n |,
$$

ここで、$N$はヒルベルト空間の基底状態の数であり、$m$はトンネリングイベントにおける励起の数です。

`sparse=true`の場合、演算子はスパース行列として返され、それ以外の場合は密行列として返されます。

!!! warning "型安定性に注意してください！"
    型安定性を保ちたい場合は、`tunneling(N, m, Val(sparse))`を使用することをお勧めします。`tunneling(N, m, sparse)`の代わりに。型安定性に関する詳細は、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type)および[関連セクション](@ref doc:Type-Stability)を参照してください。

