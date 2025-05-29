```
SLKRule(components; userlocations = String[], verbose = false)
```

## Input parameters

  * `k0`,`k`: Pair Parameter (`Float64`, optional) - Binary Interaction Parameter (no units)
  * `k1`: Pair Parameter (`Float64`, optional) - Binary Interaction Parameter (no units)
  * `l`: Pair Parameter (`Float64`,optional) - Binary Interaction Parameter (no units)

Neau's Consistent k₀,k₁,l mixing rule for Sanchez-Lacombe:

```
εᵢⱼ = √εᵢεⱼ
vᵢⱼ = (1 - lᵢⱼ)(vᵢ + vⱼ)/2
ϕᵢ = rᵢ*xᵢ/r̄
εᵣ = ΣΣϕᵢϕⱼεᵢⱼ*(1 - k₀ᵢⱼ + (1 - δᵢⱼ)(Σϕₖk₁ᵢₖ + Σϕₖk₁ₖⱼ))
vᵣ = ΣΣϕᵢϕⱼvᵢⱼ
```

Where `δᵢⱼ` is `i == j ? 1 : 0`

## References

1. Neau, E. (2002). A consistent method for phase equilibrium calculation using the Sanchez–Lacombe lattice–fluid equation-of-state. Fluid Phase Equilibria, 203(1–2), 133–140. [doi:10.1016/s0378-3812(02)00176-0](https://doi.org/10.1016/s0378-3812(02)00176-0)
