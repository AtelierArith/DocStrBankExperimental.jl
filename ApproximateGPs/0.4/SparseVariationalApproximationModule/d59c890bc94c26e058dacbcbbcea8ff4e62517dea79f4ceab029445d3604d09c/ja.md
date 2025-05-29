```
SparseVariationalApproximation(fz::FiniteGP, q::AbstractMvNormal)
```

擬似点 `fz` に対する事前分布と、擬似点での近似事後分布をパッケージ化します。これは `mean(fz) + cholesky(cov(fz)).L * ε` であり、`ε ∼ q` です。

以下の短縮形です。

```julia
SparseVariationalApproximation(NonCentered(), fz, q)
```
