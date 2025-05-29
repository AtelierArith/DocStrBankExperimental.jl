```
MSA(solvents::Array{String,1},
    ions::Array{String,1};
    RSPmodel = ConstRSP,
    userlocations = String[],
    RSPmodel_userlocations = String[],
    verbose = false)
```

## 入力パラメータ

  * `sigma`: 単一パラメータ (`Float64`) - ハードスフェア直径 `[m]`
  * `charge`: 単一パラメータ (`Float64`) - 電荷 `[-]`

## 入力モデル

  * `RSPmodel`: 相対静的誘電率モデル

## 説明

この関数は平均球近似モデルを作成するために使用されます。MSA項は、溶液中のイオン間の静電相互作用を考慮するための余剰ヘルムホルツエネルギーを与えます。

## 参考文献

1. Blum, L. (1974). Solution of a model for the solvent‐electrolyte interactions in the mean spherical approximation, 61, 2129–2133.
