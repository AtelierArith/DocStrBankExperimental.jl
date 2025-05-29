```
solidsoftSAFTModel <: SAFTModel

solidsoftSAFT(components; 
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
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー `[K]`
  * `k`: ペアパラメータ (`Float64`)（オプション） - バイナリ相互作用パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積 `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメントの数（単位なし）
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

固体相のためのソフトSAFT状態方程式。

## 参考文献

1. Johnson, J. K., Zollweg, J. A., & Gubbins, K. E. (1993). Modelling the solid–liquid–vapour phase behaviour ofn-alkanes in a TPT-1framework. Molecular physics, 78(3), 591–618. [doi:10.1080/00268979300100411](https://doi.org/10.1080/00268979300100411)
2. FELIPE J. BLAS and LOURDES F. VEGA. (1997). Thermodynamic behaviour of homonuclear and heteronuclear Lennard-Jones chains with association sites from simulation and theory. Molecular physics, 92(1), 135–150. [doi:10.1080/002689797170707](https://doi.org/10.1080/002689797170707)
3. Ramírez-Carpio, V., Galindo, A., & Gil-Villegas, A. (2023). Modelling the solid–liquid–vapour phase behaviour of n -alkanes in a TPT-1 framework. Molecular Physics, 121(19–20). [doi:10.1080/00268976.2023.2204150](https://doi.org/10.1080/00268976.2023.2204150)
