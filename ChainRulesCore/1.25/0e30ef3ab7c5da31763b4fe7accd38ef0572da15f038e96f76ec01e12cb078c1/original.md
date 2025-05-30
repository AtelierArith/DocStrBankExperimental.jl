```
@non_differentiable(signature_expression)
```

A helper to make it easier to declare that a method is not differentiable. This is a short-hand for defining an [`frule`](@ref) and [`rrule`](@ref) that return [`NoTangent()`](@ref) for all partials (even for the function `s̄elf`-partial itself)

Keyword arguments should not be included.

```jldoctest
julia> @non_differentiable Base.:(==)(a, b)

julia> _, pullback = rrule(==, 2.0, 3.0);

julia> pullback(1.0)
(NoTangent(), NoTangent(), NoTangent())
```

You can place type-constraints in the signature:

```jldoctest
julia> @non_differentiable Base.length(xs::Union{Number, Array})

julia> frule((ZeroTangent(), 1), length, [2.0, 3.0])
(2, NoTangent())
```

!!! warning
    This helper macro covers only the simple common cases. It does not support `where`-clauses. For these you can declare the `rrule` and `frule` directly

