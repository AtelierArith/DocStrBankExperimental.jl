```
SAFTgammaEMie(solvents::Array{String,1}, 
    ions::Array{String,1}; 
    idealmodel::IdealModel = BasicIdeal,
    neutralmodel::EoSModel = SAFTgammaMie,
    ionmodel::IonModel = GCMSABorn,
    RSPmodel::RSPModel = Schreckenberg,
    userlocations::Vector{String} = [],
    ideal_userlocations::Vector{String} = [],
    assoc_options::AssocOptions = AssocOptions(),
    verbose::Bool = false)
```

## 説明

この関数は、SAFT-gamma Mie、MSA、およびBornモデルの組み合わせであるSAFT-gammaE Mieモデルを作成するために使用されます。

## 入力パラメータ

### SAFT-VR Mie パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `vst`: 単一パラメータ (`Float64`) - セグメント数（単位なし）
  * `S`: 単一パラメータ (`Float64`) - セグメントの形状因子（単位なし）
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー  `[K]`
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ（単位なし）
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ（単位なし）
  * `epsilon_assoc`: 結合パラメータ (`Float64`) - 縮小結合エネルギー `[K]`
  * `bondvol`: 結合パラメータ (`Float64`) - 結合体積

### MSA パラメータ

  * `sigma`: 単一パラメータ (`Float64`) - 最接近直径 `[m]`
  * `charge`: 単一パラメータ (`Float64`) - 電荷 `[-]`

### Born パラメータ

  * `sigma_born`: 単一パラメータ (`Float64`) - Born直径 `[m]`
  * `charge`: 単一パラメータ (`Float64`) - 電荷 `[-]`

## 入力モデル

  * `idealmodel`: 理想モデル
  * `neutralmodel`: 中性EoSモデル
  * `ionmodel`: イオンモデル

## 参考文献

1. Haslam, A.J., González-Pérez, A., Di Lecce, S., Khalit, S.H., Perdomo, F.A., Kournopoulos, S., Kohns, M., Lindeboom, T., Wehbe, M., Febra, S., Jackson, G., Adjiman, C.S. & Galind, A. (2020). SAFT-γ Mieグループ寄与状態方程式の応用の拡張：混合物の熱力学的特性と相挙動の予測。Journal of Chemical Engineering Data, 65(12), 5862–5890
