```
atmosphere_emissivity(Tₐ,eₐ)
```

与えられた温度と水蒸気圧における大気の放射率。

# 引数

  * `Tₐ` (°C): 空気温度
  * `eₐ` (kPa): 空気の水蒸気圧
  * `K₀` (°C): 絶対零度

# 例

```julia
Tₐ = 20.0
VPD = 1.5
atmosphere_emissivity(Tₐ, vapor_pressure(Tₐ,VPD))
```

# 参考文献

Leuning, R., F. M. Kelliher, DGG de Pury, et E.-D. SCHULZE. 1995. Leaf nitrogen, photosynthesis, conductance and transpiration: scaling from leaves to canopies ». Plant, Cell & Environment 18 (10): 1183‑1200.
