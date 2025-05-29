```
setbit(index::Integer, mask::Integer) -> Integer
```

set the bit at masked position to 1.

# Example

```jldoctest
julia> setbit(0b1011, 0b1100) |> BitStr{4}
1111 ₍₂₎

julia> setbit(0b1011, 0b0100) |> BitStr{4}
1111 ₍₂₎

julia> setbit(0b1011, 0b0000) |> BitStr{4}
1011 ₍₂₎
```
