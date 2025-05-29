For "hard" clustering:

```
clustering_quality(data, centers, assignments; quality_index, [metric])
clustering_quality(data, clustering; quality_index, [metric])
```

For fuzzy ("soft") clustering:

```
clustering_quality(data, centers, weights; quality_index, fuzziness, [metric])
clustering_quality(data, clustering; quality_index, fuzziness, [metric])
```

For "hard" clustering without specifying cluster centers:

```
clustering_quality(data, assignments; quality_index, [metric])
clustering_quality(data, clustering; quality_index, [metric])
```

For "hard" clustering without specifying data points and cluster centers:

```
clustering_quality(assignments, dist_matrix; quality_index)
clustering_quality(clustering, dist_matrix; quality_index)
```

Compute the *quality index* for a given clustering.

Returns a quality index (real value).

## Arguments

  * `data::AbstractMatrix`: $d×n$ data matrix with each column representing one $d$-dimensional data point
  * `centers::AbstractMatrix`: $d×k$ matrix with cluster centers represented as columns
  * `assignments::AbstractVector{Int}`: $n$ vector of point assignments (cluster indices)
  * `weights::AbstractMatrix`: $n×k$ matrix with fuzzy clustering weights, `weights[i,j]` is the degree of membership of $i$-th data point to $j$-th cluster
  * `clustering::Union{ClusteringResult, FuzzyCMeansResult}`: the output of the clustering method
  * `quality_index::Symbol`: quality index to calculate; see below for the supported options
  * `dist_matrix::AbstractMatrix`: a $n×n$ pairwise distance matrix; `dist_matrix[i,j]` is the distance between $i$-th and $j$-th points

## Keyword arguments

  * `quality_index::Symbol`: clustering *quality index* to calculate; see below for the supported options
  * `fuzziness::Real`: clustering *fuzziness* > 1
  * `metric::SemiMetric=SqEuclidean()`: `SemiMetric` object that defines the metric/distance/similarity function

When calling `clustering_quality`, one can explicitly specify `centers`, `assignments`, and `weights`, or provide `ClusteringResult` via `clustering`, from which the necessary data will be read automatically.

For clustering without known cluster centers the `data` points are not required. `dist_matrix` could be provided explicitly, otherwise it would be calculated from the `data` points using the specified `metric`.

## Supported quality indices

  * `:calinski_harabasz`: hard or fuzzy Calinski-Harabsz index (↑), the corrected ratio of between cluster centers inertia and within-clusters inertia
  * `:xie_beni`: hard or fuzzy Xie-Beni index (↓), the ratio betwen inertia within clusters and minimal distance between the cluster centers
  * `:davies_bouldin`: Davies-Bouldin index (↓), the similarity between the cluster and the other most similar one, averaged over all clusters
  * `:dunn`: Dunn index (↑), the ratio of the minimal distance between clusters and the maximal cluster diameter
  * `:silhouettes`: the average silhouette index (↑), see [`silhouettes`](@ref)

The arrows ↑ or ↓ specify the direction of the incresing clustering quality. Please refer to the [documentation](@ref clustering_quality) for more details on the clustering quality indices.
