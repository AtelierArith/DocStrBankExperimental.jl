```
hclust(d::AbstractMatrix; [linkage], [uplo], [branchorder]) -> Hclust
```

Perform hierarchical clustering using the distance matrix `d` and the cluster `linkage` function.

Returns the dendrogram as a [`Hclust`](@ref) object.

# Arguments

  * `d::AbstractMatrix`: the pairwise distance matrix. $d_{ij}$ is the distance  between $i$-th and $j$-th points.
  * `linkage::Symbol`: *cluster linkage* function to use. `linkage` defines how the distances between the data points are aggregated into the distances between the clusters. Naturally, it affects what clusters are merged on each iteration. The valid choices are:

      * `:single` (the default): use the minimum distance between any of the cluster members
      * `:average`: use the mean distance between any of the cluster members
      * `:complete`: use the maximum distance between any of the members
      * `:ward`: the distance is the increase of the average squared distance of a point to its cluster centroid after merging the two clusters
      * `:ward_presquared`: same as `:ward`, but assumes that the distances in `d` are already squared.
  * `uplo::Symbol` (optional): specifies whether the upper (`:U`) or the lower (`:L`) triangle of `d` should be used to get the distances. If not specified, the method expects `d` to be symmetric.
  * `branchorder::Symbol` (optional): algorithm to order leaves and branches. The valid choices are:

      * `:r` (the default): ordering based on the node heights and the original elements order (compatible with R's `hclust`)
      * `:barjoseph` (or `:optimal`): branches are ordered to reduce the distance between neighboring leaves from separate branches using the "fast optimal leaf ordering" algorithm from [Bar-Joseph et. al. *Bioinformatics* (2001)](https://doi.org/10.1093/bioinformatics/17.suppl_1.S22)
