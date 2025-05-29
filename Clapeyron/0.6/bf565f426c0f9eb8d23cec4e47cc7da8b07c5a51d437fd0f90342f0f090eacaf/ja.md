```
PCPSAFTModel <: PCSAFTModel

const PPCSAFT = PCPSAFT

PCPSAFT(components;
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
assoc_options = AssocOptions())
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数 (単位なし)
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小した分散エネルギー `[K]`
  * `k`: ペアパラメータ (`Float64`) (オプション) - バイナリ相互作用パラメータ (単位なし)
  * `dipole`: 単一パラメータ (`Float64`) - 双極子モーメント `[D]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小したアソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積 `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数 (単位なし)
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `dipole`: 単一パラメータ (`Float64`) (オプション) - 双極子モーメント `[D]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小したアソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

摂動鎖極性SAFT (PCP-SAFT)

## 参考文献

1. Gross, J., & Vrabec, J. (2005). 極性成分の状態方程式への寄与: 双極子分子。AIChE Journal, 52(3), 856-1282. [doi:10.1002/aic.10683](https://doi.org/10.1002/aic.10683)

```
