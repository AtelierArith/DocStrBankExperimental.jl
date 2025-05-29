```
project(𝒟::Derivative, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(𝒟, domain, Float64))
```

`𝒟`を`domain`から`codomain`への[`LinearOperator`](@ref)として表現します。

関連情報: [`project!(::LinearOperator, ::Derivative)`](@ref)および[`Derivative`](@ref)。
