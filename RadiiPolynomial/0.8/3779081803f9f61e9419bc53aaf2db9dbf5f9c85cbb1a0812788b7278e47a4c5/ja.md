```
project(Δ::Laplacian, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(Δ, domain, Float64))
```

`Δ`を`domain`から`codomain`への[`LinearOperator`](@ref)として表現します。

関連情報: [`project!(::LinearOperator, ::Laplacian)`](@ref)および[`Laplacian`](@ref)。
