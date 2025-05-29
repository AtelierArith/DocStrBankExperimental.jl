A SortedVector is an AbstractVector where the underlying data is ordered (monotonically increasing).

Indexing that would unsort the data is prohibited. A SortedVector is a Dimensional axis, and no checking is done to ensure that the data is sorted. Duplicate values are allowed.

A SortedVector axis can be indexed with an ClosedInterval, with a value, or with a vector of values. Use of a SortedVector{Tuple} axis allows indexing similar to the hierarchical index of the Python Pandas package or the R data.table package.

### Constructors

```julia
SortedVector(x::AbstractVector)
```

### Keyword Arguments

  * `x::AbstractVector` : the wrapped vector

### Examples

```julia
v = SortedVector(collect([1.; 10.; 10:15.]))
A = AxisArray(reshape(1:16, 8, 2), v, [:a, :b])
A[ClosedInterval(8.,12.), :]
A[1., :]
A[10., :]

## Hierarchical index example with three key levels

data = reshape(1.:40., 20, 2)
v = collect(zip([:a, :b, :c][rand(1:3,20)], [:x,:y][rand(1:2,20)], [:x,:y][rand(1:2,20)]))
idx = sortperm(v)
A = AxisArray(data[idx,:], SortedVector(v[idx]), [:a, :b])
A[:b, :]
A[[:a,:c], :]
A[(:a,:x), :]
A[(:a,:x,:x), :]
A[ClosedInterval(:a,:b), :]
A[ClosedInterval((:a,:x),(:b,:x)), :]
```
