```
filter_expr_matrix(mat, feature_threshold, cell_threshold)
```

表現行列 `mat` をフィルタリングし、`feature_threshold` より多くの細胞で発現している遺伝子と、`cell_threshold` より多くの特徴を発現している細胞のみを保持します。フィルタリングされた行列と、特徴と細胞を保持するためのビットベクターを返します。

# 例

```jldoctest

julia> @time mat, fea, bar = read_mtx("matrix.mtx", "features.tsv", "barcodes.tsv")

julia> size(mat)
(36601, 5744)

julia> @time mat2, kf, kb = filter_expr_matrix(mat)
 26.438175 秒 (978.08 k アロケーション: 1.320 GiB, 0.52% gc 時間)
(sparse([2, 12, 15, 25, 26, 27, 29, 32, 34, 37  …  21104, 21105, 21106, 21107, 21108, 21109, 21110, 21111, 21113, 21116], [1, 1, 1, 1, 1, 1, 1, 1, 1, 1  …  5728, 5728, 5728, 5728, 5728, 5728, 5728, 5728, 5728, 5728], Int32[1, 1, 5, 1, 4, 1, 1, 1, 1, 1  …  287, 8, 239, 124, 32, 8, 145, 41, 99, 2], 21121, 5728), Bool[0, 0, 0, 1, 0, 0, 1, 0, 0, 0  …  0, 0, 0, 0, 0, 0, 0, 0, 1, 0], Bool[1, 1, 1, 1, 1, 1, 1, 1, 1, 1  …  1, 1, 1, 1, 1, 1, 1, 1, 1, 1])

julia> size(mat2)
(21121, 5728)

julia> fea2 = fea[kf]; bar2 = bar[kb];

julia> length(fea2)
21121

julia> length(bar2)
5728

```

# 引数

  * `mat::AbstractMatrix`: 表現行列（密または疎）。
  * `feature_threshold::Int`: 特徴が保持されるために発現しなければならない細胞の最小数。デフォルト: 30。
  * `cell_threshold::Int`: 細胞が保持されるために発現しなければならない遺伝子の最小数。デフォルト: 200。
