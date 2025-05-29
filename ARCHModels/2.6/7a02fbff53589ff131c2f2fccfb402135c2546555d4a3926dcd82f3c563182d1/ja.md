```
CCC{VS<:UnivariateVolatilitySpec, T<:AbstractFloat, d} <: MultivariateVolatilitySpec{T, d}
```

---

```
DCC(Qbar, coefs, univariatespecs; method=:largescale)
```

与えられたパラメータを使用してCCC仕様を構築します。`coefs`はQbarと同じ要素型の長さゼロのベクトルとして渡す必要があります。
