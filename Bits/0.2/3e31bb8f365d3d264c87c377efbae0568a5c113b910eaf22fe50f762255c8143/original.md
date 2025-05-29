```
bit(x::Integer, i::Integer)       -> typeof(x)
bit(x::AbstractFloat, i::Integer) -> Integer
```

Return the bit of `x` at position `i`, with value `0` or `1`. If `x::Integer`, the returned bit is of the same type. If `x::AbstractFloat` is a bits type, the returned bit is a signed integer with the same [`bitsize`](@ref) as `x`. See also [`tstbit`](@ref).

# Examples

```jldoctest
julia> bit(0b101, 1)
0x01

julia> bit(0b101, 2)
0x00

julia> bit(-1.0, 64)
1
```
