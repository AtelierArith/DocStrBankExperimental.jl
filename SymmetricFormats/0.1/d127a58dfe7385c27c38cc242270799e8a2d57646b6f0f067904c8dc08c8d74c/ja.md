```
SymmetricPacked(A, uplo=:U)
```

行列 `A` の上三角（`uplo = :U` の場合）または下三角（`uplo = :L` の場合）の packed 形式の `Symmetric` 行列を構築します。

# 例

```jldoctest
julia> A = [1 0 2 0 3; 0 4 0 5 0; 6 0 7 0 8; 0 9 0 1 0; 2 0 3 0 4]
5×5 Matrix{Int64}:
 1  0  2  0  3
 0  4  0  5  0
 6  0  7  0  8
 0  9  0  1  0
 2  0  3  0  4

julia> AP = SymmetricPacked(A)
5×5 SymmetricPacked{Int64, Matrix{Int64}}:
 1  0  2  0  3
 0  4  0  5  0
 2  0  7  0  8
 0  5  0  1  0
 3  0  8  0  4

julia> Base.summarysize(A)
240

julia> Base.summarysize(AP)
184
```
