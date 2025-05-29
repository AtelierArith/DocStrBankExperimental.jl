```
tstbit(x::Real, i::Integer) -> Bool
```

Similar to [`bit`](@ref) but returns the bit at position `i` as a `Bool`.

# Examples

```jldoctest
julia> tstbit(0b101, 3)
true
```
