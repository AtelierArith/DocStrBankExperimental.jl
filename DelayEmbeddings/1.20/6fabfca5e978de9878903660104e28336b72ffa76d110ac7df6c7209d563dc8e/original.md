```
Dataset{D, T} <: AbstractDataset{D,T}
```

A dedicated interface for datasets. It contains *equally-sized datapoints* of length `D`, represented by `SVector{D, T}`. These data are contained in the field `.data` of a dataset, as a standard Julia `Vector{SVector}`.

When indexed with 1 index, a `dataset` is like a vector of datapoints. When indexed with 2 indices it behaves like a matrix that has each of the columns be the timeseries of each of the variables.

`Dataset` also supports most sensible operations like `append!, push!, hcat, eachrow`, among others, and when iterated over, it iterates over its contained points.

## Description of indexing

In the following let `i, j` be integers,  `typeof(data) <: AbstractDataset` and `v1, v2` be `<: AbstractVector{Int}` (`v1, v2` could also be ranges).

  * `data[i]` gives the `i`th datapoint (returns an `SVector`)
  * `data[v1]` will return a vector of datapoints
  * `data[v1, :]` using a `Colon` as a second index will return a `Dataset` of these points
  * `data[:, j]` gives the `j`th variable timeseries, as `Vector`
  * `data[v1, v2]` returns a `Dataset` with the appropriate entries (first indices being "time"/point index, while second being variables)
  * `data[i, j]` value of the `j`th variable, at the `i`th timepoint

Use `Matrix(dataset)` or `Dataset(matrix)` to convert. It is assumed that each *column* of the `matrix` is one variable. If you have various timeseries vectors `x, y, z, ...` pass them like `Dataset(x, y, z, ...)`. You can use `columns(dataset)` to obtain the reverse, i.e. all columns of the dataset in a tuple.
