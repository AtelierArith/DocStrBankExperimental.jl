```
kmedoids(data::PopData; k::Int64, iterations::Int64 = 100, distance::PreMetric = euclidean, matrixtype::Symbol = :pca)
```

Perform Kmedoids clustering on a `PopData` object. Returns a `KmedoidsResult` object. Use the keyword argument `iterations` (default: 100) to set the maximum number of iterations allowed to achieve convergence. Interally, kmeans clustering is performed on either the principal components of the scaled allele frequencies, or just the scaled allele frequencies themselves. In both cases, `missing` values are replaced by the global mean allele frequency.

**Keyword Arguments**

  * `k`: the number of desired clusters, given as an `Integer`
  * `iterations::Int64`: the maximum number of iterations to attempt to reach convergence (default: `100`)
  * `distance`: type of distance matrix to calculate on `matrixtype` (default: `euclidean`)

      * see [Distances.jl](https://github.com/JuliaStats/Distances.jl) for a list of options (e.g. sqeuclidean, etc.)
  * `matrixtype`: type of input matrix to compute (default: `:pca`)

      * `:pca`: matrix of Principal Components
      * `:freq`: matrix of scaled allele frequencies
