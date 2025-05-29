```
Quantile(q::Vector{Float64} = [0, .25, .5, .75, 1]; b=500)
```

Calculate (approximate) quantiles from a data stream.  Internally uses [`ExpandingHist`](@ref) to estimate the distribution, for which `b` is the number of histogram bins.  Setting `b` to a larger number will increase accuracy at the cost of speed.

# Example

```
q = [.25, .5, .75]
x = randn(10^6)

o = fit!(Quantile(q, b=1000), randn(10^6))
value(o)

quantile(x, q)
```
