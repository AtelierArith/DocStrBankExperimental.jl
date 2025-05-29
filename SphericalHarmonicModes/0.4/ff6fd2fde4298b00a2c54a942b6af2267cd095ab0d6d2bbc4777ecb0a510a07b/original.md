```
LM(l_range::Union{Integer, AbstractUnitRange{<:Integer}}, m_range::Union{Integer, AbstractUnitRange{<:Integer}})
LM(l_range::Union{Integer, AbstractUnitRange{<:Integer}}, [T = FullRange]) where T<:Union{FullRange, ZeroTo, ToZero}
```

Return an iterator that loops over pairs of spherical harmonic modes `(l,m)`, with `l` increasing faster than `m`. The loop runs over all the valid modes that may be obtained from the ranges provided. If `m_range` is not specified, the loop runs over all valid values of `m` for each `l`. Neither `l_range` nor `m_range` may be empty.

Optionally `m_range` may be provided implicitly using the range specifiers [`FullRange`](@ref), [`ZeroTo`](@ref) and [`ToZero`](@ref), or as a [`SingleValuedRange`](@ref) type. Additionally, `l_range` may be of type [`ZeroTo`](@ref) or [`SingleValuedRange`](@ref). Iterators constructed using these special types would often permit optimizations.

!!! warning
    An overlarge `l_range` will be curtailed to match the valid range compatible with `m_range`. A smaller `l_range` than that compatible with `m_range` will raise an error.


# Examples

```jldoctest
julia> LM(0:1) |> collect
4-element Vector{Tuple{Int64, Int64}}:
 (1, -1)
 (0, 0)
 (1, 0)
 (1, 1)

julia> LM(0:1, 1:1) |> collect
1-element Vector{Tuple{Int64, Int64}}:
 (1, 1)

julia> r = LM(ZeroTo(1), FullRange);

julia> r |> collect
4-element Vector{Tuple{Int64, Int64}}:
 (1, -1)
 (0, 0)
 (1, 0)
 (1, 1)
```

See also: [`ML`](@ref)
