```
EGARCH{o, p, q}(coefs) -> UnivariateVolatilitySpec
```

Construct an EGARCH specification with the given parameters.

# Example:

```jldoctest
julia> EGARCH{1, 1, 1}([-0.1, .1, .9, .04])
EGARCH{1, 1, 1} specification.

─────────────────────────────────
                ω   γ₁   β₁    α₁
─────────────────────────────────
Parameters:  -0.1  0.1  0.9  0.04
─────────────────────────────────
```
