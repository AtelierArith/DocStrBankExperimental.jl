```
ARCH{q, T<:AbstractFloat} <: UnivariateVolatilitySpec{T}
```

---

```
ARCH{q}(coefs) -> UnivariateVolatilitySpec
```

Construct an ARCH specification with the given parameters.

# Example:

```jldoctest
julia> ARCH{2}([1., .3, .4])
TGARCH{0, 0, 2} specification.

──────────────────────────
               ω   α₁   α₂
──────────────────────────
Parameters:  1.0  0.3  0.4
──────────────────────────
```
