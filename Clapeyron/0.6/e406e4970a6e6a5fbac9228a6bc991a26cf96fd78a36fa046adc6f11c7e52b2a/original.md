```
SLKRule(components; userlocations = String[], verbose = false)
```

## Input parameters

  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Parameter (no units)

Constant Kᵢⱼ mixing rule for Sanchez-Lacombe:

```
εᵢⱼ = √εᵢεⱼ*(1-kᵢⱼ)
vᵢⱼ = (vᵢ + vⱼ)/2
ϕᵢ = rᵢ*xᵢ/r̄
εᵣ = ΣΣϕᵢϕⱼεᵢⱼ
vᵣ = ΣΣϕᵢϕⱼvᵢⱼ
```
