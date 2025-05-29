```
LorentzBerthelotMixing::AsymmetricMixing
LorentzBerthelotMixing(components;
userlocations = String[],
verbose = false)
```

## 入力パラメータ

  * `k`: ペアパラメータ (`Float64`) - 温度のための二項相互作用パラメータ（単位なし）
  * `l`: ペアパラメータ (`Float64`) - 体積のための二項相互作用パラメータ（単位なし）

## 説明

多パラメータEoSモデルのためのローレンツ・ベルテロ混合:

```
τ = T̄/T
δ = V̄/V
V̄ = ∑xᵢxⱼ * Vᵣᵢⱼ * (1 - lᵢⱼ)
T̄ = ∑xᵢxⱼ * Tᵣᵢⱼ * (1 - kᵢⱼ)
Vᵣᵢⱼ = 0.125*(∛Vcᵢ + ∛Vcⱼ)^3
Tᵣᵢⱼ = √(Tcᵢ*Tcⱼ)
```

欠落しているパラメータは `kᵢⱼ = lᵢⱼ = 0` と仮定されます。
