```
CCC{VS<:UnivariateVolatilitySpec, T<:AbstractFloat, d} <: MultivariateVolatilitySpec{T, d}
```

---

```
DCC(Qbar, coefs, univariatespecs; method=:largescale)
```

Construct a CCC specification with the given parameters. `coefs` must be passed as a length-zero Vector of the same element type as Qbar.
