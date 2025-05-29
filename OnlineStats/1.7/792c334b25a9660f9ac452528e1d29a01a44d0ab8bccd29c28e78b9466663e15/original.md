```
IndexedPartition(T, stat, b=100)
```

Summarize data with `stat` over a partition of size `b` where the data is indexed by a variable of type `T`.

# Example

```
x, y = randn(10^5), randn(10^6)
o = IndexedPartition(Float64, KHist(10))
fit!(o, zip(x, y))

using Plots
plot(o)
```
