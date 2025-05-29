```
differentiation_matrix(poly::AbstractPolynomial)
```

指定された多項式のノードでの微分行列を返します。

```
P = Chebyshev2{5}()
D = differentiation_matrix(P)
```

これで dy/dx ≈ `D*y` が多項式のノードで成り立ちます。
