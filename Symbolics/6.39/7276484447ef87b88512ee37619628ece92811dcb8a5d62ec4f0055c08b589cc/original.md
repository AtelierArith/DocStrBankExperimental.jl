```julia
≲(lhs, rhs) -> Any

```

Create an [`Inequality`](@ref) out of two [`Num`](@ref) instances, or an `Num` and a `Number`.

# Examples

```jldoctest
julia> using Symbolics

julia> @variables x y;

julia> x ≲ y
x ≲ y

julia> x - y ≲ 0
x - y ≲ 0
```
