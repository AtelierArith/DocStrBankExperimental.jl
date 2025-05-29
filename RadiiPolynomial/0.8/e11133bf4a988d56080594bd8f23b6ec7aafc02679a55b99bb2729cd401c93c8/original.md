```
project(ℳ::Multiplication, domain::SequenceSpace, codomain::SequenceSpace, ::Type{T}=eltype(sequence(ℳ)))
```

Represent `ℳ` as a [`LinearOperator`](@ref) from `domain` to `codomain`.

See also: [`project!(::LinearOperator{<:SequenceSpace,<:SequenceSpace}, ::Multiplication)`](@ref) and [`Multiplication`](@ref).
