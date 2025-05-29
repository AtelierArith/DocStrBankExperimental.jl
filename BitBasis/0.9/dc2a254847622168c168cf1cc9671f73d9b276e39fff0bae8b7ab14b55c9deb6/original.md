```
breflect(b::Integer[, masks::Vector{Integer}]; nbits) -> Integer
```

Return left-right reflected integer.

# Example

Reflect the order of bits.

```jldoctest
julia> breflect(0b1011; nbits=4) == 0b1101
true
```
