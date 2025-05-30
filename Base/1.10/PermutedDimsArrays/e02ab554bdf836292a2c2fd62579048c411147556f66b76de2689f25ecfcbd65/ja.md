```
permutedims(v::AbstractVector)
```

ベクトル `v` を `1 × length(v)` 行列に変形します。操作が再帰的でない点で、`LinearAlgebra` の [`transpose`](@ref) とは異なります。

# 例

```jldoctest; setup = :(using LinearAlgebra)
julia> permutedims([1, 2, 3, 4])
1×4 Matrix{Int64}:
 1  2  3  4

julia> V = [[[1 2; 3 4]]; [[5 6; 7 8]]]
2-element Vector{Matrix{Int64}}:
 [1 2; 3 4]
 [5 6; 7 8]

julia> permutedims(V)
1×2 Matrix{Matrix{Int64}}:
 [1 2; 3 4]  [5 6; 7 8]

julia> transpose(V)
1×2 transpose(::Vector{Matrix{Int64}}) with eltype Transpose{Int64, Matrix{Int64}}:
 [1 3; 2 4]  [5 7; 6 8]
```
