```
KIndexedPartition(T, stat_init, k=100)
```

Similar to [`IndexedPartition`](@ref), but indexes the first variable by centroids (like [`KHist`](@ref)) rather than intervals.

  * Note: `stat_init` must be a function e.g. `() -> Mean()`

# Example

```
using Plots

o = KIndexedPartition(Float64, () -> KHist(10))

fit!(o, zip(randn(10^6), randn(10^6)))

plot(o)
```
