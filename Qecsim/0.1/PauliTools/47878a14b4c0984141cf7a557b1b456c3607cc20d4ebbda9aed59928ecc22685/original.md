```
unpack(packed_bsf::Tuple{String,Int}) -> BitVector
```

Unpack a binary vector from a concise representation, typically from log output. See also [`pack`](@ref).

# Examples

```jldoctest
julia> a = ("2b", 6);  # (hex_value, length)

julia> b = unpack(a)  # XZY
6-element BitVector:
 1
 0
 1
 0
 1
 1
julia> pack(b) == a
true
```
