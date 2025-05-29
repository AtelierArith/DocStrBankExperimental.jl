```
Multiplication{T<:Sequence{<:SequenceSpace}} <: SpecialOperator
```

Multiplication operator associated with a given [`Sequence`](@ref).

Field:

  * `sequence :: T`

Constructor:

  * `Multiplication(::Sequence{<:SequenceSpace})`

See also: [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`mul!(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Number, ::Number)`](@ref), [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref), [`project(::Multiplication, ::SequenceSpace, ::SequenceSpace)`](@ref), [`project!(::LinearOperator{<:SequenceSpace,<:SequenceSpace}, ::Multiplication)`](@ref) and [`Multiplication`](@ref).
