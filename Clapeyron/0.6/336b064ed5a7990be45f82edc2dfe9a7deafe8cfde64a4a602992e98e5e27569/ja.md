```
SAFTVREMie(solvents::Array{String,1}, 
    ions::Array{String,1}; 
    idealmodel::IdealModel = BasicIdeal,
    neutralmodel::EoSModel = SAFTVRMie,
    ionmodel::IonModel = MSABorn,
    RSPmodel::RSPModel = Schreckenberg,
    userlocations::Vector{String} = [],
    ideal_userlocations::Vector{String} = [],
    assoc_options::AssocOptions = AssocOptions(),
    verbose::Bool = false,
    reference_state = nothing)
```

## 説明

この関数は、SAFT-VR Mie、MSA、およびBornモデルの組み合わせであるSAFT-VRE Mieモデルを作成するために使用されます。

## 入力パラメータ

### SAFT-VR Mie パラメータ

  * `Mw`: 単一パラメータ (`Float64`) - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ (`Float64`) - セグメント数（単位なし）
  * `sigma`: 単一パラメータ (`Float64`) - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ (`Float64`) - 縮小分散エネルギー  `[K]`
  * `lambda_a`: ペアパラメータ (`Float64`) - 引力範囲パラメータ（単位なし）
  * `lambda_r`: ペアパラメータ (`Float64`) - 反発範囲パラメータ（単位なし）
  * `k`: ペアパラメータ (`Float64`)（オプション） - バイナリ相互作用パラメータ（単位なし）
  * `epsilon_assoc`: 結合パラメータ (`Float64`) - 縮小結合エネルギー `[K]`
  * `bondvol`: 結合パラメータ (`Float64`) - 結合体積 `[m^3]`

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

1. Eriksen, D.K., Lazarou, G., Galindo, A., Jackson, G., Adjiman, C.S., & Haslam, A.J. (2016). Development of intermolecular potential models for electrolyte solutions using an electrolyte SAFT-VR Mie equation of state. Molecular Physics, 114(18), 2724-2749.
