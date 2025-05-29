```
BACKSAFTModel <: SAFTModel

BACKSAFT(components; 
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
assoc_options = AssocOptions())
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメント数 (単位なし)
  * `vol`: 単一パラメータ (`Float64`) - セグメント体積 [`dm^3`]
  * `epsilon`: 単一パラメータ (`Float64`) - 割減分散エネルギー  `[K/mol]`
  * `k`: ペアパラメータ (`Float64`) (オプション) - バイナリ相互作用パラメータ (単位なし)
  * `c`: 単一パラメータ (`Float64`) - 調整可能なパラメータ (単位なし)
  * `alpha`: 単一パラメータ (`Float64`) - 非球形偏差 (単位なし)

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメント数 (単位なし)
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合割減分散エネルギー`[K]`
  * `c`: 単一パラメータ (`Float64`) - 調整可能なパラメータ (単位なし)
  * `alpha`: 単一パラメータ (`Float64`) - 非球形偏差 (単位なし)

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

BACKSAFT

## 参考文献

1. Mi, J.-G., Chen, J., Gao, G.-H., & Fei, W.-Y. (2002). Equation of state extended from SAFT with improved results for polar fluids across the critical point. Fluid Phase Equilibria, 201(2), 295–307. [doi:10.1016/s0378-3812(02)00093-6](https://doi.org/10.1016/s0378-3812(02)00093-6)

```
