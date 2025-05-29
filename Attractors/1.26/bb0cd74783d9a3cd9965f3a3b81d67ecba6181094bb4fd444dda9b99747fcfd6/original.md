```
GroupViaClustering(; kwargs...)
```

Initialize a struct that contains instructions on how to group features in [`AttractorsViaFeaturizing`](@ref). `GroupViaClustering` clusters features into groups using DBSCAN, similar to the original work by bSTAB [Stender2021](@cite) and MCBB [Gelbrecht2020](@cite). Several options on clustering are available, see keywords below.

The defaults are a significant improvement over existing literature, see Description.

## Keyword arguments

  * `clust_distance_metric = Euclidean()`: A metric to be used in the clustering. It can be any function `f(a, b)` that returns the distance between real-valued vectors `a, b`. All metrics from Distances.jl can be used here.
  * `rescale_features = true`: if true, rescale each dimension of the extracted features separately into the range `[0,1]`. This typically leads to more accurate clustering.
  * `min_neighbors = 10`: minimum number of neighbors (i.e. of similar features) each feature needs to have, including counting its own self, in order to be considered in a cluster (fewer than this, it is labeled as an outlier, `-1`).
  * `use_mmap = false`: whether to use an on-disk map for creating the distance matrix of the features. Useful when the features are so many where a matrix with side their length would not fit to memory.

### Keywords for optimal radius estimation

  * `optimal_radius_method::Union{Real, String} = "silhouettes_optim"`: if a real number, it is the radius used to cluster features. Otherwise, it determines the method used to automatically determine that radius. Possible values are:

      * `"silhouettes"`: Performs a linear (sequential) search for the radius that maximizes a   statistic of the silhouette values of clusters (typically the mean). This can be chosen   with `silhouette_statistic`. The linear search may take some time to finish. To   increase speed, the number of radii iterated through can be reduced by decreasing   `num_attempts_radius` (see its entry below).
      * `"silhouettes_optim"`: Same as `"silhouettes"` but performs an optimized search via   Optim.jl. It's faster than `"silhouettes"`, with typically the same accuracy (the   search here is not guaranteed to always find the global maximum, though it typically   gets close).
      * `"knee"`: chooses the the radius according to the knee (a.k.a. elbow,   highest-derivative method) and is quicker, though generally leading to much worse   clustering. It requires that `min_neighbors` > 1.
  * `num_attempts_radius = 100`: number of radii that the `optimal_radius_method` will try out in its iterative procedure. Higher values increase the accuracy of clustering, though not necessarily much, while always reducing speed.
  * `silhouette_statistic::Function = mean`: statistic (e.g. mean or minimum) of the silhouettes that is maximized in the "optimal" clustering. The original implementation in [Stender2021](@cite) used the `minimum` of the silhouettes, and typically performs less accurately than the `mean`.
  * `max_used_features = 0`: if not `0`, it should be an `Int` denoting the max amount of features to be used when finding the optimal radius. Useful when clustering a very large number of features (e.g., high accuracy estimation of fractions of basins of attraction).

## Description

The DBSCAN clustering algorithm is used to automatically identify clusters of similar features. Each feature vector is a point in a feature space. Each cluster then basically groups points that are closely packed together. Closely packed means that the points have at least `min_neighbors` inside a ball of radius `optimal_radius` centered on them. This method typically works well if the radius is chosen well, which is not necessarily an easy task. Currently, three methods are implemented to automatically estimate an "optimal" radius.

### Estimating the optimal radius

The default method is the **silhouettes method**, which includes keywords `silhouette` and `silhouette_optim`. Both of them search for the radius that optimizes the clustering, meaning the one that maximizes a statistic `silhouette_statistic` (e.g. mean value) of a quantifier for the quality of each cluster. This quantifier is the silhouette value of each identified cluster. A silhouette value measures how similar a point is to the cluster it currently belongs to, compared to the other clusters, and ranges from -1 (worst matching) to +1 (ideal matching). If only one cluster is found, the assigned silhouette is zero. So for each attempted radius in the search the clusters are computed, their silhouettes calculated, and the statistic of these silhouettes computed. The algorithm then finds the radius that leads to the maximum such statistic. For `optimal_radius_method = "silhouettes"`, the search is done linearly, from a minimum to a maximum candidate radius for `optimal_radius_method = "silhouettes"`; `optimal_radius_method = silhouettes_optim`, it is done via an optimized search performed by Optim.jl which is typically faster and with similar accuracy. A third alternative is the`"elbow"` method, which works by calculating the distance of each point to its k-nearest-neighbors (with `k=min_neighbors`) and finding the distance corresponding to the highest derivative in the curve of the distances, sorted in ascending order. This distance is chosen as the optimal radius. It is described in [Ester1996](@cite) and [Schubert2017](@cite). It typically performs considerably worse than the `"silhouette"` methods.
