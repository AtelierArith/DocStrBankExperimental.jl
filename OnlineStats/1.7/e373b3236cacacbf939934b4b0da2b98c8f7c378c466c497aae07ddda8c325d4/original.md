```
Partition(stat)
Partition(stat, nparts)
```

Split a data stream into `nparts` (default 100) where each part is summarized by `stat`.

# Example

```
o = Partition(Extrema())
fit!(o, cumsum(randn(10^5)))

using Plots
plot(o)
```
