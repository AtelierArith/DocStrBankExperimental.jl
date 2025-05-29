```
SAFTVRMieGVModel <: SAFTModel
SAFTVRMieGV(components;
idealmodel=BasicIdeal,
userlocations=String[],
ideal_userlocations=String[],
verbose=false,
assoc_options = AssocOptions()) # SS: ここにDQ項を選択/非選択するための別のパラメータを追加することは可能ですか？
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメント数（単位なし）
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー  `[K]`
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ（単位なし）
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ（単位なし）
  * `k`: ペアパラメータ (`Float64`)（オプション） - バイナリ相互作用パラメータ（単位なし）
  * `dipole`: 単一パラメータ (`Float64`) - 双極子モーメント `[D]`
  * `np` : 単一パラメータ (`Float64`) - 双極子セグメントの数（単位なし）
  * `quadrupole`: 単一パラメータ (`Float64`) - 四重極モーメント `[DA°]`
  * `nQ` : 単一パラメータ (`Float64`) - 四重極セグメントの数（単位なし）
  * `epsilon_assoc`: 結合パラメータ (`Float64`) - 縮小結合エネルギー `[K]`
  * `bondvol`: 結合パラメータ (`Float64`) - 結合体積 `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメント数（単位なし）
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ（単位なし）
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ（単位なし）
  * `dipole`: 単一パラメータ (`Float64`) - 双極子モーメント `[D]`
  * `np` : 単一パラメータ (`Float64`) - 双極子セグメントの数（単位なし）
  * `quadrupole`: 単一パラメータ (`Float64`) - 四重極モーメント `[DA°]`
  * `nQ` : 単一パラメータ (`Float64`) - 四重極セグメントの数（単位なし）
  * `epsilon_assoc`: 結合パラメータ (`Float64`) - 縮小結合エネルギー `[K]`
  * `bondvol`: 結合パラメータ (`Float64`) - 結合体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

双極子および四重極相互作用の寄与を含む、Mieポテンシャルを用いた極性SAFT-VR（SAFT-VR Mie GV）

## 参考文献

極性項：

1. Gross, J. (2005). An equation-of-state contribution for polar components: Quadrupolar molecules. AIChE Journal, 51(9), 2556-2568. [doi:10.1002/aic.10502](https://doi.org/10.1002/aic.10502)
2. Gross, J., & Vrabec, J. (2006). An equation-of-state contribution for polar components: Dipolar molecules. AIChE Journal, 52(3), 856-1282. [doi:10.1002/aic.10683](https://doi.org/10.1002/aic.10683)
3. Gross, J., & Vrabec, J. (2008). Vapor−Liquid Equilibria Simulation and an Equation of State Contribution for Dipole−Quadrupole Interactions. J. Phys. Chem. B, 112(1), 51-60. [doi:10.1021/jp072619u](https://doi.org/10.1021/jp072619u)

SAFT-VR Mieに実装：

1. Cripwell et al. (2017). SAFT-VR-Mie with an incorporated polar term for accurate holistic prediction of the thermodynamic properties of polar components. Fluid Phase Equilibria, 455, 24-42. [doi:10.1016/j.fluid.2017.09.027](https://doi.org/10.1016/j.fluid.2017.09.027)
2. Smith et al. (2020). A Quadrupolar SAFT-VR Mie Approach to Modeling Binary Mixtures of CO2 or Benzene with n-Alkanes or 1-Alkanols. J. Chem. Eng. Data, 65(12), 5778-5800. [doi:10.1021/acs.jced.0c00705](https://doi.org/10.1021/acs.jced.0c00705)
