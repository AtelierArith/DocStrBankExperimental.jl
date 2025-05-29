```julia
struct TriMatrix{T, L<:TriMatrices.TriLayout, A} <: AbstractArray{T, 2}
```

冗長性なく連続した線形配列にデータを格納する三角行列または対称行列。
