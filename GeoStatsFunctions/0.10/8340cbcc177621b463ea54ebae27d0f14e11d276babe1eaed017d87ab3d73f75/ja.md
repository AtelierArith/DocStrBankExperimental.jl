```
structures(cov)
```

個々の構造をタプルとして返します（おそらく複合的な）共分散の。構造は、全体のナゲットと、正規化後の残りの非自明な構造の係数（または寄与）です（すなわち、sill=1、nugget=0）。

## 例

```julia
cov₁ = GaussianCovariance(nugget=1, sill=2)
cov₂ = SphericalCovariance(nugget=2, sill=3)

structures(2cov₁ + 3cov₂)
```
