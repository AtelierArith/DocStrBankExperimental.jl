```
KHist2D(b=300)
```

Approximate scatterplot of `b` centers.  This implementation is slow!  See [`IndexedPartition`](@ref) and [`KIndexedPartition`](@ref) instead.

# Example

```
x = randn(10^4)
y = x + randn(10^4)
plot(fit!(KHist2D(), zip(x, y)))
```
