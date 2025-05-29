```
SAFTVRMie15Model <: SAFTVRMieModel

SAFTVRMie(components;
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
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ (単位なし)
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ (単位なし)
  * `k`: ペアパラメータ (`Float64`) (オプション) - バイナリ相互作用パラメータ (単位なし)
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数 (単位なし)
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ (単位なし)
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ (単位なし)
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

MieポテンシャルとMieアソシエーションカーネルを用いたSAFT-VR

## 参考文献

1. Lafitte, T., Apostolakou, A., Avendaño, C., Galindo, A., Adjiman, C. S., Müller, E. A., & Jackson, G. (2013). Accurate statistical associating fluid theory for chain molecules formed from Mie segments. The Journal of Chemical Physics, 139(15), 154504. [doi:10.1063/1.4819786](https://doi.org/10.1063/1.4819786)
2. Dufal, S., Lafitte, T., Haslam, A. J., Galindo, A., Clark, G. N. I., Vega, C., & Jackson, G. (2015). The A in SAFT: developing the contribution of association to the Helmholtz free energy within a Wertheim TPT1 treatment of generic Mie fluids. Molecular Physics, 113(9–10), 948–984. [doi:10.1080/00268976.2015.1029027](https://doi.org/10.1080/00268976.2015.1029027)
