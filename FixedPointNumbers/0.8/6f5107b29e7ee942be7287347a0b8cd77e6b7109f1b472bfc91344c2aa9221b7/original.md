```
floattype(::Type{T})::Type{<:AbstractFloat}
```

Return a minimal type suitable for performing computations with instances of type `T` without integer overflow.

The fallback definition of `floattype(T)` applies only to `T<:AbstractFloat`. However, it is permissible to extend `floattype` to return types that are not subtypes of `AbstractFloat`; the key characteristic is that the return type should support computation without integer overflow.

In general the returned type should have the minimum bitwidth needed to encode the full precision of the input type. however, a priority should be placed on computational efficiency; consequently, types like `Float16` should be avoided except in scenarios where they are guaranteed to have hardware support.

# Examples

A classic usage is to avoid overflow behavior by promoting `FixedPoint` to `AbstractFloat`

```jldoctest
julia> x = N0f8(1.0)
1.0N0f8

julia> x + x # overflow
0.996N0f8

julia> T = floattype(x)
Float32

julia> T(x) + T(x)
2.0f0
```

The following represents a valid extension of `floattype` to non-AbstractFloats:

```julia
julia> using FixedPointNumbers, ColorTypes

julia> floattype(RGB{N0f8})
RGB{Float32}
```

`RGB` itself is not a subtype of `AbstractFloat`, but unlike `RGB{N0f8}` operations with `RGB{Float32}` are not subject to integer overflow.
