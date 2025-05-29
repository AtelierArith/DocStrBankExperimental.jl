```
aucell_kernel(mat, features, gene_set)
```

`mat`の各プロファイルに対して各`gene_set`のAUCを計算し、`mat`の行名は`features`として保存されており、これは`gene_set`のものと同じタイプである必要があります。

# 例

```jldoctest
julia> mat = [1 2 3;4 5 6;0 1 2;7 8 0]
4×3 Matrix{Int64}:
 1  2  3
 4  5  6
 0  1  2
 7  8  0

julia> fea = ["a", "b", "c", "d"]

julia> gene_set = ["b","c", "e"]

julia> aucell_kernel(mat, fea, gene_set)
1×3 Matrix{Float64}:
 0.125  0.125  0.5

julia> gene_sets = [["a", "b", "e"], ["b", "d", "e"]]

julia> aucell_kernel(mat, fea, gene_sets)
2×3 Matrix{Float64}:
 0.25  0.25  0.75
 0.75  0.75  0.375
```
