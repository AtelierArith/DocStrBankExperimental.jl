```
AsymmetricMixing <: MultiFluidDepartureModel
AsymmetricMixing(components;
userlocations = String[],
verbose = false)
```

## 入力パラメータ

  * `beta_v`: ペアパラメータ (`Float64`) - バイナリ相互作用パラメータ  (単位なし)
  * `gamma_v`: ペアパラメータ (`Float64`) - バイナリ相互作用パラメータ  (単位なし)
  * `beta_T`: ペアパラメータ (`Float64`) - バイナリ相互作用パラメータ  (単位なし)
  * `gamma_T`: ペアパラメータ (`Float64`) - バイナリ相互作用パラメータ  (単位なし)

## 説明

マルチパラメータEoSモデルのための非対称混合ルール：

```
τ = T̄/T
δ = V̄/V
V̄ = ∑xᵢxⱼ * βᵛᵢⱼ * γᵛᵢⱼ * (xᵢ + xⱼ)/(xᵢ*βᵛᵢⱼ^2 + xⱼ) * Vᵣᵢⱼ
T̄ = ∑xᵢxⱼ * βᵛᵢⱼ * γᵀᵢⱼ * (xᵢ + xⱼ)/(xᵢ*βᵀᵢⱼ^2 + xⱼ) * Tᵣᵢⱼ
Vᵣᵢⱼ = 0.125*(∛Vcᵢ + ∛Vcⱼ)^3
Tᵣᵢⱼ = √(Tcᵢ*Tcⱼ)
```

βパラメータに存在する非対称性：

```
βᵛᵢⱼ = 1/βᵛⱼᵢ
βᵀᵢⱼ = 1/βᵀⱼᵢ
```

データが存在しない場合、パラメータは推定できます：

  * 線形推定：

```
βᵛᵢⱼ = βᵛᵢⱼ = 1
γᵛᵢⱼ = 4*(Vcᵢ + Vcⱼ)/(∛Vcᵢ + ∛Vcⱼ)^3
γᵀᵢⱼ = 0.5*(Tcᵢ + Tcⱼ)/√(Tcᵢ*Tcⱼ)
```

  * ローレンツ・ベルテロット推定：

```
βᵛᵢⱼ = βᵛᵢⱼ = γᵛᵢⱼ = γᵀᵢⱼ = 1
```

## 参考文献

1. R. Klimeck, Ph.D. dissertation, Ruhr-Universit¨at Bochum, 2000
