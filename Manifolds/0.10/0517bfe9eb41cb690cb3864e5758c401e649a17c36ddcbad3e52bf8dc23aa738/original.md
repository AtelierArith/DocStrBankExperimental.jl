```
inner(M::SymplecticStiefel, p, X. Y)
```

Compute the Riemannian inner product $g^{\mathrm{SpSt}}$ at $p ∈ \mathrm{SpSt}$ of tangent vectors $Y, X ∈ T_p\mathrm{SpSt}$. Given by Proposition 3.10 in [BendokatZimmermann:2021](@cite).

$$
g^{\mathrm{SpSt}}_p(X, Y)
  = \operatorname{tr}\Bigl(
    X^{\mathrm{T}}\bigl(
      I_{2n} - \frac{1}{2}J_{2n}^{\mathrm{T}} p(p^{\mathrm{T}}p)^{-1}p^{\mathrm{T}}J_{2n}
    \bigr) Y (p^{\mathrm{T}}p)^{-1}\Bigr).
$$
