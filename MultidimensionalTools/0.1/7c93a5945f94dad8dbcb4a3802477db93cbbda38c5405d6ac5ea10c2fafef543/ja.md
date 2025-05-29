```
reshape_as_required(M::Array{T, N}, expand_by::T, inds::Union{Vector{NTuple{N, Int}}, Vector{CartesianIndex{N}}})
reshape_as_required(M::Array{T, N}, expand_by::T, inds::Union{NTuple{N, Int}, CartesianIndex{N}}...)
```

与えられたインデックスに基づいて、`reshape_as_required` は必要に応じて `expand_by` で行列を埋めます。もしそのようなインデックスが現在アクセスできない場合です。

```julia
julia> A = rand(Int8, 2, 2)
2×2 Array{Int8,2}:
 -96   83
 -94  -39

julia> reshape_as_required(A, zero(Int8), [(1, 1), (2, 2), (3, 3)])
3×3 Array{Int8,2}:
 -96   83  0
 -94  -39  0
   0    0  0
```
