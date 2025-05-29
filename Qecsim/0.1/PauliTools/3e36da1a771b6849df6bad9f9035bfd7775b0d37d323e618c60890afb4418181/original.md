```
pack(bsf::AbstractVector{Bool}) -> Tuple{String,Int}
```

Pack a binary vector into a concise representation, typically for log output. See also [`unpack`](@ref).

# Examples

```jldoctest
julia> a = BitVector([1, 0, 1, 0, 1, 1]);  # XZY

julia> b = pack(a)  # (hex_value, length)
("2b", 6)
julia> unpack(b) == a
true
```
