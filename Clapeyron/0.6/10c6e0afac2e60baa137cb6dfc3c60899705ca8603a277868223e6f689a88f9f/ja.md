```
DH(solvents::Array{String,1},
    ions::Array{String,1};
    RSPmodel = ConstRSP,
    userlocations = String[],
    RSPmodel_userlocations = String[],
    verbose = false)
```

## 入力パラメータ

  * `sigma`: 単一パラメータ (`Float64`) - 最接近の直径 `[m]`
  * `charge`: 単一パラメータ (`Float64`) - 電荷 `[-]`

## 入力モデル

  * `RSPmodel`: 相対静的誘電率モデル

## 説明

この関数はデバイ・ヒュッケルモデルを作成するために使用されます。デバイ・ヒュッケル項は、溶液中のイオン間の静電的相互作用を考慮するために余分なヘルムホルツエネルギーを与えます。

## 参考文献

1. Debye, P., Huckel, E. (1923). Phys. Z. 24, 185.
