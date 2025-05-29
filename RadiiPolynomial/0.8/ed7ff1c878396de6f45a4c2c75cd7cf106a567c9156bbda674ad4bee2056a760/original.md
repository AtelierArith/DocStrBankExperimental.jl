```
banach_rounding_mul!(c::Sequence{<:SequenceSpace}, a::Sequence{<:SequenceSpace}, b::Sequence{<:SequenceSpace}, X::Ell1)
```

Compute `project(banach_rounding_mul(a, b, X), space(c))` in-place. The result is stored in `c` by overwriting it.

Note: `c` must not be aliased with either `a` or `b`.

See also: [`banach_rounding_mul`](@ref), [`banach_rounding_pow`](@ref), [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`mul!(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace}, ::Number, ::Number)`](@ref) and [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref).
