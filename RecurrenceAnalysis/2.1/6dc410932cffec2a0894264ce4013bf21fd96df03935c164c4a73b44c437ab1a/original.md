```
distancematrix(x [, y = x], metric = "euclidean")
```

Create a matrix with the distances between each pair of points of the time series `x` and `y` using `metric`.

The time series `x` and `y` can be `AbstractStateSpaceSet`s or vectors or matrices with data points in rows. The data point dimensions (or number of columns) must be the same for `x` and `y`. The returned value is a `n×m` matrix, with `n` being the length (or number of rows) of `x`, and `m` the length of `y`.

The metric can be any of the `Metric`s defined in the [`Distances` package](https://github.com/JuliaStats/Distances.jl) and defaults to `Euclidean()`.
