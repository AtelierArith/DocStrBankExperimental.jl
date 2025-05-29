```
hurst_exponent(X, τ_range)
```

Calculate the Hurst exponent of the series `X` over the range `τ_range` along with its standard error.

See [Buonocore et al. 2016](https://doi.org/10.1016/j.chaos.2015.11.022).

# Examples

```jldoctest
julia> X = accumulate(+, randn(1000));

julia> isapprox(hurst_exponent(X, 1:19)[1], 0.5, atol = 0.1)
true
```
