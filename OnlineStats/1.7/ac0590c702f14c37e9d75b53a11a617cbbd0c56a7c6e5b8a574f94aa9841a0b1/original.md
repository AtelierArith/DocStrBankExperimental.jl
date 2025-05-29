```
KHist(k::Int)
```

Estimate the probability density of a univariate distribution at `k` approximately equally-spaced points.

Ref: [https://www.jmlr.org/papers/volume11/ben-haim10a/ben-haim10a.pdf](https://www.jmlr.org/papers/volume11/ben-haim10a/ben-haim10a.pdf)

A difference from the above reference is that the minimum and maximum values are not allowed to merge into another bin.

# Example

```
o = fit!(KHist(25), randn(10^6))

# Approximate statistics
using Statistics
mean(o)
var(o)
std(o)
quantile(o)
median(o)

using Plots
plot(o)
```
