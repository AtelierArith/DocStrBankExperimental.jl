`apply2upper` 関数は、`PairwiseListMatrix` の上三角部分に対して `fun` 関数を適用します。対角線をイテレーションに含める必要がある場合は、`use_diag` を `true` に設定してください。この関数は4つの引数を取ります。最初の引数は `PairwiseListMatrix` の `list` と `diag` フィールド、2番目はその `list` に対するインデックス `k`、3番目と4番目は行列の上三角部分における位置 `k` のための `i` と `j` インデックスです。

```jldoctest
julia> using PairwiseListMatrices

julia> plm = PairwiseListMatrix([1,2,3], true)
2×2 PairwiseListMatrix{Int64,true,Array{Int64,1}}:
 1  2
 2  3

julia> mat = zeros(Int, 2, 2)
2×2 Array{Int64,2}:
 0  0
 0  0

julia> apply2upper((list, k, i, j) -> mat[i, j] = list[k], plm; use_diag = true)

julia> mat
2×2 Array{Int64,2}:
 1  2
 0  3

```
