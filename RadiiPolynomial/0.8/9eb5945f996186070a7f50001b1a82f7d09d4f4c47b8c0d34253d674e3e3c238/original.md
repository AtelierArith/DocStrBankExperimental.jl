```
(ℳ::Multiplication)(a::Sequence)
```

Compute the discrete convolution (associated with `space(sequence(ℳ))` and `space(a)`) of `sequence(ℳ)` and `a`; equivalent to `sequence(ℳ) * a`.

See also: [`*(::Multiplication, ::Sequence)`](@ref), [`Multiplication`](@ref), [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`mul!(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Number, ::Number)`](@ref) and [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref).
