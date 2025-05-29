```
GARCH{p, q, T<:AbstractFloat} <: UnivariateVolatilitySpec{T}
```

---

```
GARCH{p, q}(coefs) -> UnivariateVolatilitySpec
```

Construct a GARCH specification with the given parameters.

# Example:

```jldoctest
julia> GARCH{2, 1}([1., .3, .4, .05 ])
GARCH{2, 1} specification.

────────────────────────────────
               ω   β₁   β₂    α₁
────────────────────────────────
Parameters:  1.0  0.3  0.4  0.05
────────────────────────────────
```
