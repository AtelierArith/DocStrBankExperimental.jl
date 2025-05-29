```
project(ℳ::Multiplication, domain::SequenceSpace, codomain::SequenceSpace, ::Type{T}=eltype(sequence(ℳ)))
```

`ℳ`を`domain`から`codomain`への[`LinearOperator`](@ref)として表現します。

関連情報: [`project!(::LinearOperator{<:SequenceSpace,<:SequenceSpace}, ::Multiplication)`](@ref)および[`Multiplication`](@ref)。
