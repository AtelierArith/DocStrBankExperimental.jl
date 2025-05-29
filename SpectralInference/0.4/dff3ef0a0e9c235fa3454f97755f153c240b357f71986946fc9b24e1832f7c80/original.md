```
UPGMA_tree(Dij::AbstractMatrix{<:Number})
```

shorthand for `Clustering.hclust(Dij, linkage=:average, branchorder=:optimal)`
