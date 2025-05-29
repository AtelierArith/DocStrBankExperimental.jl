```
Moments(; weight=EqualWeight())
```

First four non-central moments.

# Example

```
o = fit!(Moments(), randn(1000))
mean(o)
var(o)
std(o)
skewness(o)
kurtosis(o)
```
