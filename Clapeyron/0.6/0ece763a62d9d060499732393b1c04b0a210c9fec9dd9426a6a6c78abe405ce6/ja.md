```
SAFTVRQMieModel <: SAFTVRMieModel

SAFTVRQMie(components;
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
fh_order = :fh2,
verbose = false)
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメント数 (単位なし)
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ (単位なし)
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ (単位なし)
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー `[K]`

## モデルパラメータ

  * `Mw`: ペアパラメータ (`Float64`) - 混合分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメント数 (単位なし)
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ (単位なし)
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ (単位なし)
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

量子補正SAFT-VR Mie。特に、ファインマン–ヒッブス補正の次数は、`fh_order`キーワード引数を渡すことで変更できます。デフォルトは2次（`:fh2`）ですが、1次（`:fh1`）も利用可能です。

## 参考文献

1. Aasen, A., Hammer, M., Ervik, Å., Müller, E. A., & Wilhelmsen, Ø. (2019). Equation of state and force fields for Feynman–Hibbs-corrected Mie fluids. I. Application to pure helium, neon, hydrogen, and deuterium. The Journal of Chemical Physics, 151(6), 064508. [doi:10.1063/1.5111364](https://doi.org/10.1063/1.5111364)
2. Aasen, A., Hammer, M., Müller, E. A., & Wilhelmsen, Ø. (2020). Equation of state and force fields for Feynman-Hibbs-corrected Mie fluids. II. Application to mixtures of helium, neon, hydrogen, and deuterium. The Journal of Chemical Physics, 152(7), 074507. [doi:10.1063/1.5136079](https://doi.org/10.1063/1.5136079)
