```
ADPCSAFTModel <: SAFTModel
ADPCSAFT(components; 
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
assoc_options = AssocOptions())
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `r_c`: 単一パラメータ (`Float64`)
  * `c1`: 単一パラメータ (`Float64`)
  * `c2`: 単一パラメータ (`Float64`)
  * `c3`: 単一パラメータ (`Float64`)
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー  `[K]`
  * `k`: ペアパラメータ (`Float64`) (オプション) - バイナリ相互作用パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `theta_c`: アソシエーションパラメータ (`Float64`)

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `r_c`: 単一パラメータ (`Float64`)
  * `c1`: 単一パラメータ (`Float64`)
  * `c2`: 単一パラメータ (`Float64`)
  * `c3`: 単一パラメータ (`Float64`)
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積
  * `theta_c`: アソシエーションパラメータ (`Float64`)

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

アソシエーション依存のハードスフィア直径を持つ修正された摂動鎖SAFT (PC-SAFT)。現在は水のみに対応しています。

!!! 警告 "数値的に不安定"     その機能形式のため、DAPTは数値的に不安定です。ほとんどの計算には `big` Floats を使用してください。

## 参考文献

1. Marshall, B. D. (2021). A modified perturbed chain‐statistical associating fluid theory equation of state for water which includes an association dependent hard sphere diameter. AIChE Journal. American Institute of Chemical Engineers, 67(10). [doi:10.1002/aic.17342](https://doi.org/10.1002/aic.17342)
