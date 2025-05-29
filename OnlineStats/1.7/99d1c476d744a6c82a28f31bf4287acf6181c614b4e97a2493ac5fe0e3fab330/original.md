```
Ash(h::Union{KHist, Hist, ExpandingHist})
Ash(h::Union{KHist, Hist, ExpandingHist}, m::Int, kernel::Function)
```

Create an Average Shifted Histogram using `h` as the base histogram with smoothing parameter `m` and kernel function `kernel`.  Built-in kernels are available in the `OnlineStats.Kernels` module.

# Example

```
using OnlineStats, Plots

o = fit!(Ash(ExpandingHist(1000)), randn(10^6))

plot(o)
plot(o, 20)
plot(o, OnlineStats.Kernels.epanechnikov, 4)
```
