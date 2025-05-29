```
filter_expr_matrix(mat, feature_threshold, cell_threshold)
```

Filter an expression matrix `mat`, only keep those genes expressed in greater than `feature_threshold` cells and cells expressing greater than `cell_threshold` features. Return the filtered matrix and the bit vectors for keeping features and cells.

# Examples

```jldoctest

julia> @time mat, fea, bar = read_mtx("matrix.mtx", "features.tsv", "barcodes.tsv")

julia> size(mat)
(36601, 5744)

julia> @time mat2, kf, kb = filter_expr_matrix(mat)
 26.438175 seconds (978.08 k allocations: 1.320 GiB, 0.52% gc time)
(sparse([2, 12, 15, 25, 26, 27, 29, 32, 34, 37  …  21104, 21105, 21106, 21107, 21108, 21109, 21110, 21111, 21113, 21116], [1, 1, 1, 1, 1, 1, 1, 1, 1, 1  …  5728, 5728, 5728, 5728, 5728, 5728, 5728, 5728, 5728, 5728], Int32[1, 1, 5, 1, 4, 1, 1, 1, 1, 1  …  287, 8, 239, 124, 32, 8, 145, 41, 99, 2], 21121, 5728), Bool[0, 0, 0, 1, 0, 0, 1, 0, 0, 0  …  0, 0, 0, 0, 0, 0, 0, 0, 1, 0], Bool[1, 1, 1, 1, 1, 1, 1, 1, 1, 1  …  1, 1, 1, 1, 1, 1, 1, 1, 1, 1])

julia> size(mat2)
(21121, 5728)

julia> fea2 = fea[kf]; bar2 = bar[kb];

julia> length(fea2)
21121

julia> length(bar2)
5728

```

# Arguments

  * `mat::AbstractMatrix`: expression matrix (either dense or sparse).
  * `feature_threshold::Int`: the least number of cells that a feature must express in, in order to be kept. Default: 30.
  * `cell_threshold::Int`: the least number of genes that a cell must express, in order to be kept. Default: 200.
