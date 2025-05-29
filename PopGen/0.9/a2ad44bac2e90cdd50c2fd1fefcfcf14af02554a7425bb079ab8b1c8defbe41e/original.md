```
fuzzycmeans(data::PopData; c::Int64, fuzziness::Int64 = 2, iterations::Int64 = 100, matrixtype::Symbol = :pca)
```

An expansion of `Clustering.fuzzy_cmeans` (from Clustering.jl) to perform Fuzzy C-means clustering on a PopData object. This is a convenience method which converts the `PopData` object to either an allele frequency or PCA matrix, and performs Fuzzy C-means clustering on the Euclidean distance matrix of that. Returns a `FuzzyCMeansResult` object, which contains the assignment weights in the `.weights` field.

**Keyword Arguments**

  * `c`: the number of desired clusters, given as an `Integer`
  * `fuzziness::Integer`: clusters' fuzziness, must be >1 (default: `2`)

      * a fuzziness of 2 is common for systems with unknown numbers of clusters
  * `iterations::Int64`: the maximum number of iterations to attempt to reach convergence (default: `100`)
  * `matrixtype`: type of input matrix to compute (default: `:pca`)

      * `:pca`: matrix of Principal Components
      * `:freq`: matrix of scaled allele frequencies
