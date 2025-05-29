```
BlockedArray{T, N, R} <: AbstractBlockArray{T, N}
```

A `BlockedArray` is similar to a [`BlockArray`](@ref) except the full array is stored contiguously instead of block by block. This means that is not possible to insert and retrieve blocks without copying data. On the other hand `parent` on a `BlockedArray` is instead instant since it just returns the wrapped array.

When iteratively solving a set of equations with a gradient method the Jacobian typically has a block structure. It can be convenient to use a `BlockedArray` to build up the Jacobian block by block and then pass the resulting matrix to a direct solver using `parent`.

# Examples

```jldoctest
julia> A = zeros(Int, 2, 3);

julia> B = BlockedArray(A, [1,1], [2,1])
2×2-blocked 2×3 BlockedMatrix{Int64}:
 0  0  │  0
 ──────┼───
 0  0  │  0

julia> parent(B) === A
true

julia> B[Block(1,1)] .= 4
1×2 view(::Matrix{Int64}, 1:1, 1:2) with eltype Int64:
 4  4

julia> A
2×3 Matrix{Int64}:
 4  4  0
 0  0  0
```
