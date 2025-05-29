```
@bit_str -> BitStr64
```

Construct a bit string. such as `bit"0000"`. The bit strings also supports string `join`. Just use it like normal strings.

## Example

```jldoctest
julia> bit"10001"
10001 ₍₂₎

julia> bit"100_111_101"
100111101 ₍₂₎

julia> join(bit"1001", bit"11", bit"1110")
1001111110 ₍₂₎

julia> onehot(bit"1001")
16-element Vector{ComplexF64}:
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 1.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im

```
