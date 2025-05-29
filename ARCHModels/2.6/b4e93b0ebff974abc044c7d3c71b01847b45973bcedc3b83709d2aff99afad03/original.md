```
UnivariateARCHModel(spec::UnivariateVolatilitySpec, data::Vector; dist=StdNormal(),
          			meanspec=NoIntercept(), fitted=false
          			)
```

Create a UnivariateARCHModel.

# Example:

```jldoctest
julia> UnivariateARCHModel(GARCH{1, 1}([1., .9, .05]), randn(10))

GARCH{1, 1} model with Gaussian errors, T=10.


─────────────────────────────────────────
                             ω   β₁    α₁
─────────────────────────────────────────
Volatility parameters:     1.0  0.9  0.05
─────────────────────────────────────────
```
