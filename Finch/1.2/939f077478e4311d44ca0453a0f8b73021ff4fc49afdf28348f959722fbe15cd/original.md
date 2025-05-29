```
fspzeros([type], M...)
```

Create a random zero tensor of size `M`, with elements of type `type`. The tensor is in COO format.

See also: (`spzeros`)(https://docs.julialang.org/en/v1/stdlib/SparseArrays/#SparseArrays.spzeros)

# Examples

```jldoctest
julia> A = fspzeros(Bool, 3, 3)
3×3 Tensor{SparseCOOLevel{2, Tuple{Int64, Int64}, Vector{Int64}, Tuple{Vector{Int64}, Vector{Int64}}, ElementLevel{false, Bool, Int64, Vector{Bool}}}}:
 0  0  0
 0  0  0
 0  0  0

julia> countstored(A)
0

julia> B = fspzeros(Float64, 2, 2, 2)
2×2×2 Tensor{SparseCOOLevel{3, Tuple{Int64, Int64, Int64}, Vector{Int64}, Tuple{Vector{Int64}, Vector{Int64}, Vector{Int64}}, ElementLevel{0.0, Float64, Int64, Vector{Float64}}}}:
[:, :, 1] =
 0.0  0.0
 0.0  0.0

[:, :, 2] =
 0.0  0.0
 0.0  0.0

julia> countstored(B)
0

```
