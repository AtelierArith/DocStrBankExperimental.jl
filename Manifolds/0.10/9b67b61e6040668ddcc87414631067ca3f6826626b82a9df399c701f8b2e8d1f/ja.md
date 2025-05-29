```
Random.rand(M::DeterminantOneMatrices; vector_at=nothing, kwargs...)
```

`vector_at` が `nothing` の場合、埋め込み内の `rand` を使用して、[`DeterminantOneMatrices`](@ref) 多様体 `M` 上のランダムな点を返します。

`vector_at` が `nothing` でない場合、埋め込み内の `rand` を使用して、[`DeterminantOneMatrices`](@ref) の点 `vector_at` の接空間からランダムな接ベクトルを返します。
