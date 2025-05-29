```
DAPTModel <: SAFTModel
DAPT(components; 
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
  * `lambda`: 単一パラメータ (`Float64`)
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー  `[K]`
  * `k`: ペアパラメータ (`Float64`)（オプション） - バイナリ相互作用パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `theta_c`: アソシエーションパラメータ (`Float64`)

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `r_c`: 単一パラメータ (`Float64`)
  * `lambda`: 単一パラメータ (`Float64`)
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `theta_c`: アソシエーションパラメータ (`Float64`)

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

二重アソシエーション摂動理論モデル。現在のところ水にのみ対応しています。

!!! warning "数値的に不安定"
    その機能的形式のため、DAPTは数値的に不安定です。ほとんどの計算には `big` Floats を使用してください。


## 参考文献

1. Marshall, B. D. (2019). A doubly associated reference perturbation theory for water. Fluid Phase Equilibria, 500(112252), 112252. [doi:10.1016/j.fluid.2019.112252](https://doi.org/10.1016/j.fluid.2019.112252)
