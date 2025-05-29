```
LJSAFTModel <: SAFTModel

LJSAFT(components;
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
  * `b`: 単一パラメータ (`Float64`) - セグメント体積 [`dm^3/mol`]
  * `T_tilde`: 単一パラメータ (`Float64`) - レナード・ジョーンズ引力パラメータ  `[K]`
  * `k`: ペアパラメータ (`Float64`)（オプション） - エネルギーのためのバイナリ相互作用パラメータ（単位なし）
  * `zeta`: ペアパラメータ (`Float64`) - 体積のためのバイナリ相互作用パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 削減アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積 `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `b`: ペアパラメータ (`Float64`) - 混合セグメント共体積 `[dm^3/mol]`
  * `T_tilde`: ペアパラメータ (`Float64`) - 混合レナード・ジョーンズ引力パラメータ `[K]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 削減アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

摂動鎖SAFT (PC-SAFT)

## 参考文献

1. Kraska, T., & Gubbins, K. E. (1996). Phase equilibria calculations with a modified SAFT equation of state. 1. Pure alkanes, alkanols, and water. Industrial & Engineering Chemistry Research, 35(12), 4727–4737. [doi:10.1021/ie9602320](https://doi.org/10.1021/ie9602320)

```
