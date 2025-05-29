```
AuroraKNN(;kKNN=1000, loocv=true, tree=KDTree,
           pca=false, pca_dimension=false)
```

Aurora with `k`-Nearest neighbors.  If `looc=false`, then `k` is chosen equal to `kKNN`, while if `loocv=true`, then `k` is selected for each held-out replicate by Leave-One-Out Cross-validation among the choices 1,...,`kKNN`.

`tree` describes the nearest neighbor computation strategy. The following options are available: `:auto`, as well as , `:kdtree`, `:balltree` and `:brutetree` from the `NearestNeighbors.jl` package.

If `pca=true`, a dimension reduction strategy is employed to find nearest neighbors using PCA (principal component analysis). For each held-out replicate, the order statistics are projected into the principal component subspace of dimension `pca_dimension`. Note that in this case, the resulting nearest neighbors may only be interpreted as approximate nearest neighbors.
