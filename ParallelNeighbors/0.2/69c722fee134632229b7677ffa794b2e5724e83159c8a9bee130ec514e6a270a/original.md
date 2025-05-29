```
knn(Xtrain, Xtest, k, batch_size; metric, convert, algorithm)
```

Interface to all parallel implementations to determine the nearest neighbors of a number of points, where each column in `Xtrain` and `Xtest` corresponds to a point.

## Parameters

```
Xtrain::M where M <: AbstractMatrix{<:AbstractFloat}
```

Matrix of training points.

```
Xtest::M where M <: AbstractMatrix{<:AbstractFloat}
```

Matrix of test points.

```
k::Int
```

Nuumber of nearest neighbors to find in the training points.

```
batch_size::Int
```

Batch size to split the training and/or test data.

```
metric::PreMetric
```

(Pre-) Metric to use for distance computation.

```
convert::Function
```

Conversion function to convert the input data (`Xtrain` and `Xtest`) to an appropriate format, e.g. `CUDA.cu`.

```
algorithm::Symbol
```

The specific algorithm to use to determine the nearest neighbors.
