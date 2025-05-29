```
Variance(T = Float64; weight=EqualWeight())
```

Univariate variance, tracked as type `T`.

# Example

```
o = fit!(Variance(), randn(10^6))
mean(o)
var(o)
std(o)
```
