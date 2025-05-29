```
structures(γ)
```

個々の構造をタプルとして返します（おそらく複合的な）バリオグラムの。構造は、全体のナゲットと、正規化後の残りの非自明な構造の係数（または寄与）です（すなわち、シル=1、ナゲット=0）。

## 例

```julia
γ₁ = GaussianVariogram(nugget=1, sill=2)
γ₂ = SphericalVariogram(nugget=2, sill=3)

structures(2γ₁ + 3γ₂)
```
