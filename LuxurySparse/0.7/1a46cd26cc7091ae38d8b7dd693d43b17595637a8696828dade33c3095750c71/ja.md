```
PermMatrix{Tv, Ti}(perm::AbstractVector{Ti}, vals::AbstractVector{Tv}) where {Tv, Ti<:Integer}
PermMatrix(perm::Vector{Ti}, vals::Vector{Tv}) where {Tv, Ti}
PermMatrix(ds::AbstractMatrix)
```

PermMatrixは特別な種類の線形演算子を表します：Permute and Multiply、つまり `M * v = v[perm] * val`です。`inv` と `*` の最適化された実装により、`SparseMatrixCSC` よりもはるかに高速です。

  * `perm` は置換順序です。
  * `vals` は乗算因子です。

[Generalized Permutation Matrix](https://en.wikipedia.org/wiki/Generalized_permutation_matrix)

# 例

```julia-repl
julia> PermMatrix([2,1,4,3], rand(4))
4×4 SDPermMatrix{Float64, Int64, Vector{Float64}, Vector{Int64}}:
 0.0       0.182251  0.0      0.0
 0.887485  0.0       0.0      0.0
 0.0       0.0       0.0      0.182831
 0.0       0.0       0.22895  0.0

```
