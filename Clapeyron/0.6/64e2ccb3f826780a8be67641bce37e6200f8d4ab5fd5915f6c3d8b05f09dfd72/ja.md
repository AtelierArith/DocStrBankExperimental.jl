```
QuadraticDeparture <: MultiFluidDepartureModel
QuadraticDeparture(components;
userlocations = String[],
verbose = false)
```

## 入力パラメータ

  * `k0`: ペアパラメータ (`Float64`) - バイナリ相互作用パラメータ（単位なし）
  * `k1`: ペアパラメータ (`Float64`) - バイナリ、T依存の相互作用パラメータ `[K^-1]`

## 説明

二次混合則を使用した出発：

```
aᵣ = ∑xᵢxⱼaᵣᵢⱼ
aᵣᵢⱼ = 0.5*(aᵣᵢ + aᵣⱼ)*(1 - (k₀ + k₁T))
```

## 参考文献

1. Jäger, A., Breitkopf, C., & Richter, M. (2021). The representation of cross second virial coefficients by multifluid mixture models and other equations of state. Industrial & Engineering Chemistry Research, 60(25), 9286–9295. [doi:10.1021/acs.iecr.1c01186](https://doi.org/10.1021/acs.iecr.1c01186)
