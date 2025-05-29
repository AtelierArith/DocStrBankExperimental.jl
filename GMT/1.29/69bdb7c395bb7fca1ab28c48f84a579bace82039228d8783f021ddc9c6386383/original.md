```
Ik = kmeans(I::GMTimage, k=5; seeds=nothing, maxiter=100, tol=1e-7, V=false) -> GMTimage
```

Compute a k-means clustering on an RGB image `I`. It produces a fixed number of clusters, each associated with a center, and each RGB color is assigned to a cluster with the nearest center.

  * `I`: The input $GMTimage$ object.
  * `k`: The number of clusters when using unsupervised classification.
  * `seeds`: For supervised classifications this is Mx3 UInt8 matrix with the colors of the cluster centers. The algorithm than aggregates  all colors in the image around these M seed colors. Attention, if provided, this option resets `k`.
  * `maxiter`: Maximum number of iterations that the algorithm may run till reach a solution.
  * `tol`: Alternatively, sets the minimal allowed change of the objective during convergence. The iteration process stops when one of the two conditions is met first.
  * `V`: Print some info at the end of the iterative loop (number of iterations, time spent).

```
kmeans(X::Union{GMTdataset, Matrix{<:Real}}, k=3; seeds=nothing, maxiter=100, tol=1e-7,
       raw::Bool=false, V=false) -> Vector{GMTdataset} | idx, centers, counts
```

This method accepts a M-by-d matrix or a $GMTdataset$ where columns represent the data points and rows the `d`-dimensional data point.

  * `raw`: A Boolean that if `false` makes the return data be a vector of $GMTdatset$, one for each cluster found in input data. If `raw=true`, we return: `idx, centers, counts`, where

      * `idx`: A vector of ints with the assignments of each data points (by position in the `idx` vector) to clusters.
      * `centers`: A k-by-d matrix with the centers of each cluster.
      * `counts`: A matrix of integers with the cluster number in first column, and number of elements in that cluster in second column.

### Example

```jldoctest
    D = gmtread(GMT.TESTSDIR * "iris.dat");
	Dk = kmeans(D, k=3)		# Unsupervised segment data into 3 clusters.
```
