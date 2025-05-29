```
rand(::AbstractLieGroup; vector_at=nothing, σ::Real=1.0, kwargs...)
rand(::AbstractLieGroup, PT::Type; vector_at=nothing, σ::Real=1.0, kwargs...)
rand!(::LieAlgebra, T::Type; σ::Real=1.0, kwargs...)
rand!(::AbstractLieGroup, gX::PT; vector_at=nothing, σ::Real=1.0, kwargs...)
rand!(::LieAlgebra, X::T; σ::Real=1.0, kwargs...)
```

リー群上のランダムな点または接ベクトルを計算します。

点の場合、これは基礎となる多様体上のランダムな点を生成することを意味します。

接ベクトルの場合、リー代数の要素が生成されます。詳細は[`rand(::LieAlgebra; kwargs...)`](@ref)を参照してください。

どちらの場合も、特定の表現でランダムな点を生成したい場合は、接ベクトルおよび/または点$PT$の型$T$を提供できます。インプレースバリアントの場合、型はそれぞれ`pX´および`X`から推論されます。
