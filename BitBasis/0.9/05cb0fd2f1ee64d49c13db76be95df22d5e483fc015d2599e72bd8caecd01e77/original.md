```
flip(index::Integer, mask::Integer) -> Integer
```

Return an Integer with bits at masked position flipped.

# Example

```jldoctest
julia> flip(0b1011, 0b1011) |> BitStr{4}
0000 ₍₂₎
```
