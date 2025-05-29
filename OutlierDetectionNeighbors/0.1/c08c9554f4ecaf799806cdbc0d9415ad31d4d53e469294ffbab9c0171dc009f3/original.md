```
COFDetector(k = 5,
            metric = Euclidean(),
            algorithm = :kdtree,
            leafsize = 10,
            reorder = true,
            parallel = false)
```

Local outlier density based on chaining distance between graphs of neighbors, as described in [1].

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

## Examples

```julia
using OutlierDetection: COFDetector, fit, transform
detector = COFDetector()
X = rand(10, 100)
model, result = fit(detector, X; verbosity=0)
test_scores = transform(detector, model, X)
```

## References

[1] Tang, Jian; Chen, Zhixiang; Fu, Ada Wai-Chee; Cheung, David Wai-Lok (2002): Enhancing Effectiveness of Outlier Detections for Low Density Patterns.
