```
SLKRule(components; userlocations = String[], verbose = false)
```

## 入力パラメータ

  * `k`: ペアパラメータ (`Float64`) (オプション) - バイナリ相互作用パラメータ (単位なし)

サンチェス・ラコームの定数 Kᵢⱼ 混合則:

```
εᵢⱼ = √εᵢεⱼ*(1-kᵢⱼ)
vᵢⱼ = (vᵢ + vⱼ)/2
ϕᵢ = rᵢ*xᵢ/r̄
εᵣ = ΣΣϕᵢϕⱼεᵢⱼ
vᵣ = ΣΣϕᵢϕⱼvᵢⱼ
```
