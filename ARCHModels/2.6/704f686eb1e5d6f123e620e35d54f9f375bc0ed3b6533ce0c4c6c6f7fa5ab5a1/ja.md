```
ARCH{q, T<:AbstractFloat} <: UnivariateVolatilitySpec{T}
```

---

```
ARCH{q}(coefs) -> UnivariateVolatilitySpec
```

与えられたパラメータでARCH仕様を構築します。

# 例:

```jldoctest
julia> ARCH{2}([1., .3, .4])
TGARCH{0, 0, 2} 仕様。

──────────────────────────
               ω   α₁   α₂
──────────────────────────
パラメータ:  1.0  0.3  0.4
──────────────────────────
```
