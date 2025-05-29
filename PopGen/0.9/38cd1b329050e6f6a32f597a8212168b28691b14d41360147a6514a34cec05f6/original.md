```julia
cluster(::PopData, method::Function ; kwargs)
```

A convenience wrapper to perform clustering on a `PopData` object determined by a designated `method` (see below). The chosen method must also be supplied with the appropriate keyword arguments for that method. For more information on  a specific method, see its docstring with `?methodname`

**Clustering Methods**

  * `kmeans`: K-means++ clustering

      * kwargs: `k`, `iterations`, `matrixtype`
  * `kmedoids`: K-medoids clustering

      * kwargs: `k`, `iterations`, `distance`, `matrixtype`
  * `hclust`: Hierarchical clustering

      * kwargs: `linkage`, `branchorder`, `distance`, `matrixtype`
  * `fuzzycmeans`: Fuzzy C-means lustering

      * kwargs: `c`, `fuzziness`, `iterations`, `matrixtype`
  * `dbscan`: Density-based Spatial Clustering of Applications with Noise (DBSCAN)

      * kwargs: `radius`, `minpoints`, `distance`, `matrixtype`
