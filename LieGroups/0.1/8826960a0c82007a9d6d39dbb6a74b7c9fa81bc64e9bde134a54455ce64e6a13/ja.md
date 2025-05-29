```
rand(::LieGroup; vector_at=nothing, σ=1.0, kwargs...)
rand(::LieAlgebra; σ=1.0, kwargs...)
rand!(::AbstractLieGroup, gX; vector_at=nothing, kwargs...)
rand!(::LieAlgebra, X; σ=1.0, kwargs...)
```

リー群上のランダムな点または接ベクトルを計算します。

点の場合、これは基礎となる多様体上のランダムな点を生成することを意味します。

接ベクトルの場合、リー代数の要素が生成されます。詳細は[`rand(::LieAlgebra; kwargs...)`](@ref)を参照してください。
