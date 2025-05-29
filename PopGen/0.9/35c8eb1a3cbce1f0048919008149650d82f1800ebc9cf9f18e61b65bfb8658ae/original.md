```
dbscan(::PopData; radius::Float64, minpoints::Int64 = 2, distance::PreMetric = euclidean, matrixtype::Symbol = :pca)
```

An expansion of `Clustering.dbscan` (from Clustering.jl) to perform Density-based Spatial Clustering of Applications with Noise (DBSCAN) on a PopData object. This is a convenience method which converts the `PopData` object to either an allele frequency or PCA matrix, and performs DBSCAN clustering on the distance matrix of that. Returns a `DbscanResult` object, which contains the assignments in the `.assignments` field.

**Keyword Arguments**

  * `radius::Float64`: the radius of a point neighborhood
  * `minpoints::Int`: the minimum number of a core point neighbors (default: `2`)
  * `distance`: type of distance matrix to calculate on `matrixtype` (default: `euclidean`)

      * see [Distances.jl](https://github.com/JuliaStats/Distances.jl) for a list of options (e.g. sqeuclidean, etc.)
  * `matrixtype`: type of input matrix (default: `:pca`)

      * `:pca`: matrix of Principal Components
      * `:freq`: matrix of allele frequencies
