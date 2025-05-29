```
CovMatrix(p=0; weight=EqualWeight())
CovMatrix(::Type{T}, p=0; weight=EqualWeight())
```

Calculate a covariance/correlation matrix of `p` variables.  If the number of variables is unknown, leave the default `p=0`.

# Example

```
o = fit!(CovMatrix(), randn(100, 4) |> eachrow)
cor(o)
cov(o)
mean(o)
var(o)
```
