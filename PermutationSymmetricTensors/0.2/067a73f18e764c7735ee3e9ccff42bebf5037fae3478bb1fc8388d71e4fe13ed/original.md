function find*degeneracy(N::Int, dim::Int)  function find*degeneracy(::SymmetricTensor{T, N, dim}) where {dim, N, T}  function find*degeneracy(N, dim, full*indices)

```
returns a SymmetricTensor{Int64, N, dim} of which each element specifies the number of index permutations that point to the same element. 
for efficiency can be called with the result of `find_degeneracy(N, dim)` as a third argument.

Examples: 
julia> find_degeneracy(3, 3)
3×3×3 SymmetricTensor{Int64, 3, 3}:
[:, :, 1] =
1  3  3
3  3  6
3  6  3

[:, :, 2] =
3  3  6
3  1  3
6  3  3

[:, :, 3] =
3  6  3
6  3  3
3  3  1

julia> a = rand(SymmetricTensor{Float64, 2,4});

julia> find_degeneracy(a)
2×2×2×2 SymmetricTensor{Int64, 2, 4}:
[:, :, 1, 1] =
1  4
4  6

[:, :, 2, 1] =
4  6
6  4

[:, :, 1, 2] =
4  6
6  4

[:, :, 2, 2] =
6  4
4  1
```
