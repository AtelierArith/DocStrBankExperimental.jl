```
banach_rounding_mul(a::Sequence{<:SequenceSpace}, b::Sequence{<:SequenceSpace}, X::Ell1)
```

Compute the discrete convolution (associated with `space(a)` and `space(b)`) of `a` and `b`. A cut-off order is estimated such that the coefficients of the output beyond this order are rigorously enclosed.

See also: [`banach_rounding_mul!`](@ref), [`banach_rounding_pow`](@ref), [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`mul!(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Number, ::Number)`](@ref) and [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref).
