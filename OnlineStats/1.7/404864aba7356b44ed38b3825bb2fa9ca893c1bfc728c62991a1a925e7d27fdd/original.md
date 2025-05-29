```
OrderStats(b::Int, T::Type = Float64; weight=EqualWeight())
```

Average order statistics with batches of size `b`.

# Example

```
o = fit!(OrderStats(100), randn(10^5))
quantile(o, [.25, .5, .75])

f = ecdf(o)
f(0)
```
