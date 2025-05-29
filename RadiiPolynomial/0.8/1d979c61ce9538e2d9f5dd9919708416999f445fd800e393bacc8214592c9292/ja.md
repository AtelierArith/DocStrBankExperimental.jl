```
project(𝒮::Shift, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(𝒮, domain, Float64))
```

`𝒮`を`domain`から`codomain`への[`LinearOperator`](@ref)として表現します。

関連情報: [`project!(::LinearOperator, ::Shift)`](@ref)および[`Shift`](@ref)。
