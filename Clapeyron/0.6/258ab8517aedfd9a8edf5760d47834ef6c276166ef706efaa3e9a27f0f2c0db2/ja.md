```
CKSAFTModel <: SAFTModel

CKSAFT(components; 
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
  * `vol`: 単一パラメータ (`Float64`) - セグメント体積 [`dm^3`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー  `[K]`
  * `k`: ペアパラメータ (`Float64`) (オプション) - バイナリ相互作用パラメータ（単位なし）
  * `c`: 単一パラメータ (`Float64`) - 分散T依存パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積 `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `c`: 単一パラメータ (`Float64`) - 分散T依存パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

Chen and Kreglewski SAFT (CK-SAFT)

## 参考文献

1. Huang, S. H., & Radosz, M. (1990). Equation of state for small, large, polydisperse, and associating molecules. Industrial & Engineering Chemistry Research, 29(11), 2284–2294. [doi:10.1021/ie00107a014](https://doi.org/10.1021/ie00107a014)
2. Huang, S. H., & Radosz, M. (1991). Equation of state for small, large, polydisperse, and associating molecules: extension to fluid mixtures. Industrial & Engineering Chemistry Research, 30(8), 1994–2005. [doi:10.1021/ie00056a050](https://doi.org/10.1021/ie00056a050)

```
