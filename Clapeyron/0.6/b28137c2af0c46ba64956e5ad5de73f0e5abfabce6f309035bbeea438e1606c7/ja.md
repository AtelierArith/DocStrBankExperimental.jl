```
SLKRule(components; userlocations = String[], verbose = false)
```

## 入力パラメータ

  * `k0`,`k`: ペアパラメータ (`Float64`, オプション) - バイナリ相互作用パラメータ（単位なし）
  * `k1`: ペアパラメータ (`Float64`, オプション) - バイナリ相互作用パラメータ（単位なし）
  * `l`: ペアパラメータ (`Float64`, オプション) - バイナリ相互作用パラメータ（単位なし）

Neauの一貫したk₀,k₁,l混合則（Sanchez-Lacombe用）:

```
εᵢⱼ = √εᵢεⱼ
vᵢⱼ = (1 - lᵢⱼ)(vᵢ + vⱼ)/2
ϕᵢ = rᵢ*xᵢ/r̄
εᵣ = ΣΣϕᵢϕⱼεᵢⱼ*(1 - k₀ᵢⱼ + (1 - δᵢⱼ)(Σϕₖk₁ᵢₖ + Σϕₖk₁ₖⱼ))
vᵣ = ΣΣϕᵢϕⱼvᵢⱼ
```

ここで `δᵢⱼ` は `i == j ? 1 : 0`

## 参考文献

1. Neau, E. (2002). A consistent method for phase equilibrium calculation using the Sanchez–Lacombe lattice–fluid equation-of-state. Fluid Phase Equilibria, 203(1–2), 133–140. [doi:10.1016/s0378-3812(02)00176-0](https://doi.org/10.1016/s0378-3812(02)00176-0)
