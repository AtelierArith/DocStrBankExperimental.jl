```
neg(index::Integer, nbits::Int) -> Integer
```

Return an integer with all bits flipped (with total number of bit `nbits`).

# Example

```jldoctest
julia> neg(0b1111, 4) |> BitStr{4}
0000 ₍₂₎

julia> neg(0b0111, 4) |> BitStr{4}
1000 ₍₂₎
```
