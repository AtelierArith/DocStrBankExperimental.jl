```
KNNDetector(k=5,
            metric=Euclidean,
            algorithm=:kdtree,
            leafsize=10,
            reorder=true,
            reduction=:maximum)
```

Calculate the anomaly score of an instance based on the distance to its k-nearest neighbors.

## Parameters

```
k::Integer
```

Number of neighbors (must be greater than 0).

```
metric::Metric
```

This is one of the Metric types defined in the Distances.jl package. It is possible to define your own metrics by creating new types that are subtypes of Metric.

```
algorithm::Symbol
```

One of `(:kdtree, :balltree)`. In a `kdtree`, points are recursively split into groups using hyper-planes. Therefore a KDTree only works with axis aligned metrics which are: Euclidean, Chebyshev, Minkowski and Cityblock. A *brutetree* linearly searches all points in a brute force fashion and works with any Metric. A *balltree* recursively splits points into groups bounded by hyper-spheres and works with any Metric.

```
static::Union{Bool, Symbol}
```

One of `(true, false, :auto)`. Whether the input data for fitting and transform should be statically or dynamically allocated. If `true`, the data is statically allocated. If `false`, the data is dynamically allocated. If `:auto`, the data is dynamically allocated if the product of all dimensions except the last is greater than 100.

```
leafsize::Int
```

Determines at what number of points to stop splitting the tree further. There is a trade-off between traversing the tree and having to evaluate the metric function for increasing number of points.

```
reorder::Bool
```

While building the tree this will put points close in distance close in memory since this helps with cache locality. In this case, a copy of the original data will be made so that the original data is left unmodified. This can have a significant impact on performance and is by default set to true.

```
parallel::Bool
```

Parallelize `score` and `predict` using all threads available. The number of threads can be set with the `JULIA_NUM_THREADS` environment variable. Note: `fit` is not parallel.

```
reduction::Symbol
```

One of `(:maximum, :median, :mean)`. (`reduction=:maximum`) was proposed by [1]. Angiulli et al. [2] proposed sum to reduce the distances, but mean has been implemented for numerical stability.

## Examples

```julia
using OutlierDetection: KNNDetector, fit, transform
detector = KNNDetector()
X = rand(10, 100)
model, result = fit(detector, X; verbosity=0)
test_scores = transform(detector, model, X)
```

## References

[1] Ramaswamy, Sridhar; Rastogi, Rajeev; Shim, Kyuseok (2000): Efficient Algorithms for Mining Outliers from Large Data Sets.

[2] Angiulli, Fabrizio; Pizzuti, Clara (2002): Fast Outlier Detection in High Dimensional Spaces.
