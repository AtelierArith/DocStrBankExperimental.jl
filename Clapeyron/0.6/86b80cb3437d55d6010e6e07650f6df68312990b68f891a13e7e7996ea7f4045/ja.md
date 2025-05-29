```
CritExtrapolationSaturation <: SaturationMethod
CritExtrapolationSaturation(;crit = nothing)
```

臨界点から液体と蒸気の体積を外挿する飽和法。外挿は次のように定義されます：

```
ρₓ = ρc ± sqrt(6* Tc * (Tc - T)/Tc * ∂²p∂ρ∂T / ∂³p∂ρ³)
```

この方法は、T > 0.999Tc のときに液体と蒸気の体積を計算するのに特に便利です。

## 参考文献

1. Bell, I. H., & Deiters, U. K. (2023). Superancillary equations for nonpolar pure fluids modeled with the PC-SAFT equation of state. Industrial & Engineering Chemistry Research. [doi:10.1021/acs.iecr.2c02916](https://doi.org/10.1021/acs.iecr.2c02916)
