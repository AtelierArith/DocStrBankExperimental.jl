```
project(ℐ::Integral, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(ℐ, domain, Float64))
```

`ℐ`を`domain`から`codomain`への[`LinearOperator`](@ref)として表現します。

関連情報: [`project!(::LinearOperator, ::Integral)`](@ref)および[`Integral`](@ref)を参照してください。
