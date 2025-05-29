```
CPPCSAFTModel <: PCSAFTModel

CPPCSAFT(components; 
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
  * `k`: ペアパラメータ (`Float64`) (オプション) - バイナリ相互作用パラメータ (単位なし)
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積 `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: ペアパラメータ (`Float64`) - セグメントの数 (単位なし)
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

クリティカルポイントベースのPC-SAFT (CP-PC-SAFT)

## 参考文献

1. Polishuk, I. (2014). 標準化されたクリティカルポイントベースの統計的アソシエーション流体理論パラメータの数値解法: 変形チェーン-統計的アソシエーション流体理論状態方程式の再考. Industrial & Engineering Chemistry Research, 53(36), 14127–14141. [doi:10.1021/ie502633e](https://doi.org/10.1021/ie502633e)

```
