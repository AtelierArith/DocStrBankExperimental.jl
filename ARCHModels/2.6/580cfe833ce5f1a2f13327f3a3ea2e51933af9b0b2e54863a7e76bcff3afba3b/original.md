```
TGARCH{o, p, q}(coefs) -> UnivariateVolatilitySpec
```

Construct a TGARCH specification with the given parameters.

# Example:

```jldoctest
julia> TGARCH{1, 1, 1}([1., .04, .9, .01])
TGARCH{1, 1, 1} specification.

─────────────────────────────────
               ω    γ₁   β₁    α₁
─────────────────────────────────
Parameters:  1.0  0.04  0.9  0.01
─────────────────────────────────
```
