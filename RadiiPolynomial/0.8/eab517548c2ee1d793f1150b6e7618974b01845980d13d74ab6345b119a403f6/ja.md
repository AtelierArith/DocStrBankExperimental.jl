```
project(ℰ::Evaluation, domain::VectorSpace, codomain::VectorSpace, ::Type{T}=_coeftype(ℰ, domain, Float64))
```

`ℰ`を`domain`から`codomain`への[`LinearOperator`](@ref)として表現します。

関連情報: [`project!(::LinearOperator, ::Evaluation)`](@ref)および[`Evaluation`](@ref)を参照してください。
