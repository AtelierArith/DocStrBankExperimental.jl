```
DHBorn(solvents::Array{String,1},
    ions::Array{String,1};
    RSPmodel = ConstRSP,
    userlocations = String[],
    RSPmodel_userlocations = String[],
    verbose = false)
```

## 入力パラメータ

  * `sigma`: 単一パラメータ (`Float64`) - 最接近の直径 `[m]`
  * `sigma_born`: 単一パラメータ (`Float64`) - ボルン直径 `[m]`
  * `charge`: 単一パラメータ (`Float64`) - 電荷 `[-]`

## 入力モデル

  * `RSPmodel`: 相対静的誘電率モデル

## 説明

この関数は、デバイ・ヒュッケル・ボルンモデルを作成するために使用されます。デバイ・ヒュッケル・ボルン項は、溶液中のイオン間の静電的相互作用を考慮するための余剰ヘルムホルツエネルギーを与えます。

## 参考文献

1. Debye, P., Huckel, E. (1923). Phys. Z. 24, 185.
2. Born, M. (1920). Z. Phys. 1, 45.
