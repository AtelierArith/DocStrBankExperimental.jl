```
hclust(data::PopData; linkage::Symbol = :single, branchorder::Symbol = :r, distance::PreMetric = euclidean, matrixtype::Symbol = :pca)
```

An expansion of `Clustering.hclust` (from Clustering.jl) to perform hierarchical clustering on a PopData object. This is a convenience method which converts the `PopData` object to either an allele frequency or PCA matrix, converts that into a distance matrix, and performs hierarchical clustering on that distance matrix. Returns an `Hclust` object, which contains many metrics but does not include cluster assignments. Use  `cutree(::PopData, ::Hclust; krange...)` to compute the sample assignments for a range of `k` clusters.

**Keyword Arguments**

  * `linkage`: defines how the distances between the data points are aggregated into the distances between the clusters (default: `:single`)

      * `:single`: use the minimum distance between any of the cluster members
      * `:average`: use the mean distance between any of the cluster members
      * `:complete`: use the maximum distance between any of the members
      * `:ward`: the distance is the increase of the average squared distance of a point to its cluster centroid after merging the two clusters
      * `:ward_presquared`: same as `:ward`, but assumes that the distances in the distance matrix are already squared.
  * `branchorder`: algorithm to order leaves and branches (default: `:r`)

      * `:r`: ordering based on the node heights and the original elements order (compatible with R's hclust)
      * `:optimal`: branches are ordered to reduce the distance between neighboring leaves from separate branches using the "fast optimal leaf ordering" [algorithm](https://doi.org/10.1093/bioinformatics/17.suppl_1.S22)
  * `distance`: type of distance matrix to calculate on `matrixtype` (default: `euclidean`)

      * see [Distances.jl](https://github.com/JuliaStats/Distances.jl) for a list of options (e.g. sqeuclidean, etc.)
  * `matrixtype`: type of input matrix (default: `:pca`)

      * `:pca`: matrix of Principal Components
      * `:freq`: matrix of allele frequencies
