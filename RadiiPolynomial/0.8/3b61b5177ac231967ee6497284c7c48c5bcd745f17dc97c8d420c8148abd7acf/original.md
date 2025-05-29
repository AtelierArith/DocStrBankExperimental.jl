```
mul!(c::Sequence{<:SequenceSpace}, a::Sequence{<:SequenceSpace}, b::Sequence{<:SequenceSpace}, α::Number, β::Number)
```

Compute `project(a * b, space(c)) * α + c * β` in-place. The result is stored in `c` by overwriting it.

Note: `c` must not be aliased with either `a` or `b`.

See also: [`*(::Sequence{<:SequenceSpace}, ::Sequence{<:SequenceSpace})`](@ref), [`^(::Sequence{<:SequenceSpace}, ::Int)`](@ref), [`banach_rounding_mul`](@ref), [`banach_rounding_mul!`](@ref) and [`banach_rounding_pow`](@ref).
