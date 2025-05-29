```
inner(M::SymplecticStiefel, p, X. Y)
```

接触ベクトル $Y, X ∈ T_p\mathrm{SpSt}$ のリーマン内積 $g^{\mathrm{SpSt}}$ を $p ∈ \mathrm{SpSt}$ で計算します。これは [BendokatZimmermann:2021](@cite) の命題 3.10 によって与えられます。

$$
g^{\mathrm{SpSt}}_p(X, Y)
  = \operatorname{tr}\Bigl(
    X^{\mathrm{T}}\bigl(
      I_{2n} - \frac{1}{2}J_{2n}^{\mathrm{T}} p(p^{\mathrm{T}}p)^{-1}p^{\mathrm{T}}J_{2n}
    \bigr) Y (p^{\mathrm{T}}p)^{-1}\Bigr).
$$
