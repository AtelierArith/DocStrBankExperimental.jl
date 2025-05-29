```
structSAFTgammaMie <: SAFTgammaMieModel

structSAFTgammaMie(components; 
idealmodel = BasicIdeal,
userlocations = String[],
group_userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
epsilon_mixing = :default,
assoc_options = AssocOptions())
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `vst`: 単一パラメータ (`Float64`) - セグメント数（単位なし）
  * `S`: 単一パラメータ (`Float64`) - セグメントの形状因子（単位なし）
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー `[K]`
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ（単位なし）
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## モデルパラメータ

  * `segment`: 単一パラメータ (`Float64`) - セグメント数（単位なし）
  * `shapefactor`: 単一パラメータ (`Float64`) - セグメントの形状因子（単位なし）
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ（単位なし）
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ（単位なし）
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積
  * `mixed_segment`: 混合グループ寄与パラメータ: ∑nᵢₖνₖmₖ

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

s-SAFT-γ-Mie EoS

## 参考文献

1. Shaahmadi,, F., Hurter, R.M., Burger, A.J., Cripwell, J.T. (2021). Improving the SAFT-γ Mie equation of state to account for functional group interactions in a structural (s-SAFT-γ Mie) framework: Linear and branched alkanes. The Journal of Chemical Physics, 154, 244102. [doi:10.1063/5.0048315 ](https://doi.org/10.1063/5.0048315 )
2. Schulze-Hulbe, A., Shaahmadi, F., Burger, A.J., Cripwell, J.T. (2022). Extending the Structural (s)-SAFT-γ Mie Equation of State to Primary Alcohols. Industrial & Engineering Chemistry Research, 61 (33), 12208-12228. [doi:10.1021/acs.iecr.2c00198](https://doi.org/10.1021/acs.iecr.2c00198)

```
