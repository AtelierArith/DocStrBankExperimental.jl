```
SAFTVRSWModel <: SAFTModel

SAFTVRSW(components;
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
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー  `[K]`
  * `lambda`: 単一パラメータ (`Float64`) - ソフトウェル範囲パラメータ (単位なし)
  * `k`: ペアパラメータ (`Float64`) (オプション) - バイナリ相互作用パラメータ (単位なし)
  * `l`: ペアパラメータ (`Float64`) (オプション) - バイナリ相互作用パラメータ (単位なし)
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積 `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数 (単位なし)
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `lambda`: ペアパラメータ (`Float64`) - 混合ソフトウェル範囲パラメータ (単位なし)
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

SAFT, 可変範囲 (VR), 正方形井戸 (SW)

## 参考文献

1. Gil-Villegas, A., Galindo, A., Whitehead, P. J., Mills, S. J., Jackson, G., & Burgess, A. N. (1997). Statistical associating fluid theory for chain molecules with attractive potentials of variable range. The Journal of chemical physics, 106(10), 4168–4186. [doi:10.1063/1.473101](https://doi.org/10.1063/1.473101)

```
