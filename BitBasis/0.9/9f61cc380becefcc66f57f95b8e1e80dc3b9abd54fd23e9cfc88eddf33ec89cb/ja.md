```
@bit_str -> BitStr64
```

ビット文字列を構築します。例えば `bit"0000"` のように。ビット文字列は文字列の `join` もサポートしています。通常の文字列のように使ってください。

## 例

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
