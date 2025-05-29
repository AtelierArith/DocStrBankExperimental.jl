```
KahanVariance(; T=Float64, weight=EqualWeight())
```

Track the univariate variance. Uses compensation terms for a higher accuracy.

#Note

This should be more accurate as [`Variance`](@ref) in most cases but the guarantees of [`KahanSum`](@ref) do not apply. [`merge!`](@ref) can have accuracy issues.

# Example

```
o = fit!(KahanVariance(), randn(10^6))
mean(o)
var(o)
std(o)
```
