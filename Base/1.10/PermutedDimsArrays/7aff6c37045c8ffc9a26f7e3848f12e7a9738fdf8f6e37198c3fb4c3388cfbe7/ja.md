```
permutedims(A::AbstractArray, perm)
```

配列 `A` の次元を入れ替えます。`perm` は、次元の入れ替えを指定する長さ `ndims(A)` のベクトルまたはタプルです。

関連項目として [`permutedims!`](@ref)、[`PermutedDimsArray`](@ref)、[`transpose`](@ref)、[`invperm`](@ref) を参照してください。

# 例

```jldoctest
julia> A = reshape(Vector(1:8), (2,2,2))
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

[:, :, 2] =
 5  7
 6  8

julia> perm = (3, 1, 2); # 最後の次元を最初に持ってくる

julia> B = permutedims(A, perm)
2×2×2 Array{Int64, 3}:
[:, :, 1] =
 1  2
 5  6

[:, :, 2] =
 3  4
 7  8

julia> A == permutedims(B, invperm(perm)) # 逆順序
true
```

`B = permutedims(A, perm)` の各次元 `i` に対して、`A` の対応する次元は `perm[i]` になります。これは、`size(B, i) == size(A, perm[i])` が成り立つことを意味します。

```jldoctest
julia> A = randn(5, 7, 11, 13);

julia> perm = [4, 1, 3, 2];

julia> B = permutedims(A, perm);

julia> size(B)
(13, 5, 11, 7)

julia> size(A)[perm] == ans
true
```
