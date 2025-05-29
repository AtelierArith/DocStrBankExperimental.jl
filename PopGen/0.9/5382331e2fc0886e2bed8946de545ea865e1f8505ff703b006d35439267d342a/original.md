```
kmeans(data::PopData; k::Int64, iterations::Int64 = 100, matrixtype::Symbol = :pca)
```

Perform Kmeans clustering (using Kmeans++) on a `PopData` object. Returns a `KmeansResult` object. Use the keyword argument `iterations` (default: 100) to set the maximum number of iterations allowed to achieve convergence. Interally, kmeans clustering is performed on either the principal components of the scaled allele frequencies, or just the scaled allele frequencies themselves. In both cases, `missing` values are replaced by the global mean allele frequency.

**Keyword Arguments**

  * `k`: the number of desired clusters, given as an `Integer`
  * `iterations::Int64`: the maximum number of iterations to attempt to reach convergence (default: `100`)
  * `matrixtype`: type of input matrix to compute (default: `:pca`)

      * `:pca`: matrix of Principal Components
      * `:freq`: matrix of scaled allele frequencies

**Example**

```julia
julia> cats = @nancycats ;

julia> km = kmeans(cats, k = 2)
```
