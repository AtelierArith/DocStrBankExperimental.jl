```
gcPCPSAFTModel <: PCSAFTModel

HeterogcPCPSAFT(components; 
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
assoc_options = AssocOptions())
```

## 入力パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `m`: 単一パラメータ (`Float64`) - セグメント数（単位なし）
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー `[K]`
  * `dipole`: 単一パラメータ (`Float64`) - 双極子モーメント `[D]`
  * `k`: ペアパラメータ (`Float64`) - バイナリ相互作用パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積 `[m^3]`

## モデルパラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメント数（単位なし）
  * `sigma`: ペアパラメータ (`Float64`) - 混合セグメント直径 `[m]`
  * `epsilon`: ペアパラメータ (`Float64`) - 混合縮小分散エネルギー`[K]`
  * `dipole`: 単一パラメータ (`Float64`) - 双極子モーメント `[D]`
  * `epsilon_assoc`: アソシエーションパラメータ (`Float64`) - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ (`Float64`) - アソシエーション体積

## 入力モデル

  * `idealmodel`: 理想モデル

## 説明

ヘテロセグメントグループ寄与極性摂動鎖SAFT (Hetero-gc-PCP-SAFT)

## 参考文献

1. Gross, J., Spuhl, O., Tumakaka, F. & Sadowski, G. (2003). Modeling Copolymer Systems Using the Perturbed-Chain SAFT Equation of State. Industrial & Engineering Chemistry Research, 42, 1266-1274. [doi:10.1021/ie020509y](https://doi.org/10.1021/ie020509y)
2. Sauer, E., Stavrou, M. & Gross, J. (2014). Comparison between a Homo- and a Heterosegmented Group Contribution Approach Based on the Perturbed-Chain Polar Statistical Associating Fluid Theory Equation of State. Industrial & Engineering Chemistry Research, 53(38), 14854–14864. [doi:10.1021/ie502203w](https://doi.org/10.1021/ie502203w)

## 利用可能なグループのリスト

|       名前 |             説明 |
| --------:| --------------:|
|      CH3 |            メチル |
|      CH2 |           メチレン |
|       CH |                |
|        C |                |
|     CH2= |         終端アルケン |
|      CH= |                |
|      =C< |                |
|     C#CH |         終端アルキン |
| cCH2_pen | サイクリックペンタングループ |
|  cCH_pen |                |
| cCH2_hex | サイクリックヘキサングループ |
|  cCH_hex |                |
|      aCH |        芳香族グループ |
|      aCH |                |
|       OH |     ヒドロキシルグループ |
|      NH2 |        アミングループ |

```
