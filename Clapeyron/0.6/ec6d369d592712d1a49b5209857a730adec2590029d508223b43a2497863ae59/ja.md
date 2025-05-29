GEDeparture <: MultiFluidDepartureModel     GEDeparture(components;     activity = UNIFAC,     userlocations = String[],     verbose = false)

## 入力パラメータ

なし

  * `k1`: ペアパラメータ (`Float64`) - バイナリ、T依存の相互作用パラメータ `[K^-1]`

## モデルパラメータ

  * `vref`: 単一パラメータ (`Float64`, 計算済み) - 参照純モル体積 `[m3/mol]`

## 入力モデル

  * `activity`: 活動モデル

## 説明

活動モデルからの残余過剰ギブズエネルギーを使用する出発点:

```
aᵣ = ∑xᵢaᵣᵢ(δ,τ) + Δa
Δa = gᴱᵣ/RT - log(1+bρ)/log(1+bρref) * ∑xᵢ(aᵣᵢ(δref,τ) - aᵣᵢ(δrefᵢ,τᵢ))
τᵢ = Tcᵢ/T
δref = ρref/ρr
δrefᵢ = ρrefᵢ/ρcᵢ
b = 1/1.17ρref
```

## 参考文献

1. Jäger, A., Breitkopf, C., & Richter, M. (2021). The representation of cross second virial coefficients by multifluid mixture models and other equations of state. Industrial & Engineering Chemistry Research, 60(25), 9286–9295. [doi:10.1021/acs.iecr.1c01186](https://doi.org/10.1021/acs.iecr.1c01186)
