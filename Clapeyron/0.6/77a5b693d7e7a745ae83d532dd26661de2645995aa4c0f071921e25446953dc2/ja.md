```
SanchezLacombe(components;
idealmodel = BasicIdeal,
mixing = SLk0k1lMixingRule,
userlocations = String[],
ideal_userlocations = String[],
mixing_userlocations = String[],
reference_state = false,
verbose = false)
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `epsilon`: 単一パラメータ (`Float64`) - モノマーあたりの非結合相互作用エネルギー `[J/mol]`
  * `vol`: 単一パラメータ (`Float64`) - 密閉充填された特定体積 `[m^3/mol]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `epsilon`: ペアパラメータ (`Float64`) - モノマーあたりの非結合相互作用エネルギー `[J/mol]`
  * `vol`: ペアパラメータ (`Float64`) - 密閉充填された特定体積 `[m^3/mol]`

## 入力モデル

  * `idealmodel`: 理想モデル
  * `mixing`: 混合モデル

## 説明

サンチェス・ラコーム格子流体状態方程式。

```
xᵢ = zᵢ/∑zᵢ
r̄ = ∑xᵢrᵢ
vᵣ,εᵣ = mix_vε(model,V,T,z,model.mixing,r̄,∑zᵢ)
ρ̃ = r̄*vᵣ/v
T̃ = R̄*T/εᵣ
aᵣ = r̄*(- ρ̃ /T̃ + (1/ρ̃  - 1)*log(1 - ρ̃ ) + 1)
```

## 参考文献

1. Neau, E. (2002). A consistent method for phase equilibrium calculation using the Sanchez–Lacombe lattice–fluid equation-of-state. Fluid Phase Equilibria, 203(1–2), 133–140. [doi:10.1016/s0378-3812(02)00176-0](https://doi.org/10.1016/s0378-3812(02)00176-0)
