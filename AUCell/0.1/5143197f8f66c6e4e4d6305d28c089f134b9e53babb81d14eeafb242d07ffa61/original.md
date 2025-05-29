```
aucell_kernel(mat, features, gene_set)
```

Calculate the AUC  for each `gene_set` in each profile of `mat` and row names of `mat` are stored as `features` which should be the same types with those in `gene_set`.

# Examples

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
