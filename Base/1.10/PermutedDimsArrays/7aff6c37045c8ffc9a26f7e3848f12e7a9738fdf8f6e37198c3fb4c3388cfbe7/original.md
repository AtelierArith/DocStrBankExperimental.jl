```
permutedims(A::AbstractArray, perm)
```

Permute the dimensions of array `A`. `perm` is a vector or a tuple of length `ndims(A)` specifying the permutation.

See also [`permutedims!`](@ref), [`PermutedDimsArray`](@ref), [`transpose`](@ref), [`invperm`](@ref).

# Examples

```jldoctest
julia> A = reshape(Vector(1:8), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

julia> perm = (3, 1, 2); # put the last dimension first

julia> B = permutedims(A, perm)
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 5  6

[:, :, 2] =
 3  4
 7  8

julia> A == permutedims(B, invperm(perm)) # the inverse permutation
true
```

For each dimension `i` of `B = permutedims(A, perm)`, its corresponding dimension of `A` will be `perm[i]`. This means the equality `size(B, i) == size(A, perm[i])` holds.

```jldoctest
julia> A = randn(5, 7, 11, 13);

julia> perm = [4, 1, 3, 2];

julia> B = permutedims(A, perm);

julia> size(B)
(13, 5, 11, 7)

julia> size(A)[perm] == ans
true
```
