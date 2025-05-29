```
ogSAFTModel <: SAFTModel

ogSAFT(components;
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
assoc_options = AssocOptions())
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー  `[K]`
  * `k`: ペアパラメータ (`Float64`)（オプション） - バイナリ相互作用パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積 `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

（原文）統計的アソシエーティング流体理論（og-SAFT）状態方程式

## 参考文献

1. Chapman, W. G., Gubbins, K. E., Jackson, G., & Radosz, M. (1989). SAFT: Equation-of-state solution model for associating fluids. Fluid Phase Equilibria, 52, 31–38. [doi:10.1016/0378-3812(89)80308-5](https://doi.org/10.1016/0378-3812(89)80308-5)
2. Chapman, W. G., Gubbins, K. E., Jackson, G., & Radosz, M. (1990). New reference equation of state for associating liquids. Industrial & Engineering Chemistry Research, 29(8), 1709–1721. [doi:10.1021/ie00104a021](https://doi.org/10.1021/ie00104a021)
