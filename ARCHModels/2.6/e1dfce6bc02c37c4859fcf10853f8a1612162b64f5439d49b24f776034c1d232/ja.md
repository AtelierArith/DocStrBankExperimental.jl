```
GARCH{p, q, T<:AbstractFloat} <: UnivariateVolatilitySpec{T}
```

---

```
GARCH{p, q}(coefs) -> UnivariateVolatilitySpec
```

指定されたパラメータでGARCH仕様を構築します。

# 例:

```jldoctest
julia> GARCH{2, 1}([1., .3, .4, .05 ])
GARCH{2, 1} 仕様。

────────────────────────────────
               ω   β₁   β₂    α₁
────────────────────────────────
パラメータ:  1.0  0.3  0.4  0.05
────────────────────────────────
```
