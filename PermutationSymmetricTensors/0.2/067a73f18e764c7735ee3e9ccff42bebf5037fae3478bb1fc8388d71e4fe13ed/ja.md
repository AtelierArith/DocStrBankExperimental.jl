function find*degeneracy(N::Int, dim::Int)  function find*degeneracy(::SymmetricTensor{T, N, dim}) where {dim, N, T}  function find*degeneracy(N, dim, full*indices)

```
SymmetricTensor{Int64, N, dim}を返し、各要素は同じ要素を指すインデックスの順列の数を指定します。
効率のために、第三引数として`find_degeneracy(N, dim)`の結果を渡すことができます。

例:
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
