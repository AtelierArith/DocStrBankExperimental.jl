```
SAFTVRSMieModel <: SAFTModel

SAFTVRSMie(components;
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

WCA摂動理論を用いた固体相のためのMieポテンシャルを持つSAFT-VR。

## 参考文献

1. Jalani, Y., Ramrattana, N., Walker, P.J., Riedemann, A., Galindo, A., Mater, O. K., & Müller, E. A. (2024). SAFT-VR Mie Equation of State for the Solid and Fluid Phases. (準備中)
