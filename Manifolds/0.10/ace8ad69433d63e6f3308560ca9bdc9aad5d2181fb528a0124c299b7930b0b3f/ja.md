```
rand(::GroupManifold; vector_at=nothing, σ=1.0)
rand!(::GroupManifold, pX; vector_at=nothing, kwargs...)
rand(::TraitList{<:IsGroupManifold}, M; vector_at=nothing, σ=1.0)
rand!(TraitList{<:IsGroupManifold}, M, pX; vector_at=nothing, kwargs...)
```

リー群上のランダムな点または接ベクトルを計算します。

点の場合、これは基礎となる多様体自体上のランダムな点を生成することを意味します。

接ベクトルの場合、リー代数の要素が生成されます。
