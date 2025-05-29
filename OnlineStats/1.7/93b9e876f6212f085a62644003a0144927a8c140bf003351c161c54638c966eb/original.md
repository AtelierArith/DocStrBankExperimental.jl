```
KahanMean(; T=Float64, weight=EqualWeight())
```

Track a univariate mean. Uses a compensation term for the update.

#Note

This should be more accurate as [`Mean`](@ref) in most cases but the guarantees of [`KahanSum`](@ref) do not apply. [`merge!`](@ref) can have some accuracy issues.

# Update

$μ = (1 - γ) * μ + γ * x$

# Example

```
@time fit!(KahanMean(), randn(10^6))
```
