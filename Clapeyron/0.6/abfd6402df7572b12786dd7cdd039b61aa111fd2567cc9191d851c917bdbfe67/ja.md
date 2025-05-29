```
ePCSAFT(solvents::Array{String,1}, 
    ions::Array{String,1}; 
    idealmodel::IdealModel = BasicIdeal,
    neutralmodel::EoSModel = pharmaPCSAFT,
    ionmodel::IonModel = DH,
    RSPmodel::RSPModel = ConstRSP,
    userlocations::Vector{String} = [],
    ideal_userlocations::Vector{String} = [],
    assoc_options::AssocOptions = AssocOptions(),
    verbose::Bool = false,
    reference_state = nothing)
```

## 説明

この関数は、PC-SAFTとデバイ・ヒュッケルモデルの組み合わせであるePCSAFTモデルを作成するために使用されます。これは、ePC-SAFT改訂版に基づいています。

## 入力パラメータ

### PC-SAFTパラメータ

  * `Mw`: 単一パラメータ（`Float64`） - 分子量 `[g/mol]`
  * `segment`: 単一パラメータ（`Float64`） - セグメントの数（単位なし）
  * `sigma`: 単一パラメータ（`Float64`） - セグメント直径 [`A°`]
  * `epsilon`: 単一パラメータ（`Float64`） - 縮小分散エネルギー  `[K]`
  * `k`: ペアパラメータ（`Float64`）（オプション） - バイナリ相互作用パラメータ（単位なし）
  * `epsilon_assoc`: アソシエーションパラメータ（`Float64`） - 縮小アソシエーションエネルギー `[K]`
  * `bondvol`: アソシエーションパラメータ（`Float64`） - アソシエーション体積 `[m^3]`

### デバイ・ヒュッケルパラメータ

  * `sigma`: 単一パラメータ（`Float64`） - 最接近の直径 `[m]`
  * `charge`: 単一パラメータ（`Float64`） - 電荷 `[-]`

## 入力モデル

  * `idealmodel`: 理想モデル
  * `neutralmodel`: 中性EoSモデル
  * `ionmodel`: イオンモデル

## 参考文献

1. Held, C., Reschke, T., Mohammad, S., Luza, A., Sadowski, G. (2014). ePC-SAFT Revised. Chemical Engineering Research and Design, 92(12), 2884-2897.
