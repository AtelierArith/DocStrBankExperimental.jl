```
Born(solvents::Array{String,1},
    salts::Array{String,1};
    RSPmodel = ConstRSP,
    userlocations = String[],
    RSPmodel_userlocations = String[],
    verbose = false)
```

## 入力パラメータ

  * `sigma_born`: 単一パラメータ (`Float64`) - ボルン直径 `[m]`
  * `charge`: 単一パラメータ (`Float64`) - 電荷 `[-]`

## 入力モデル

  * `RSPmodel`: 相対静的誘電率モデル

## 説明

この関数はボルンモデルを作成するために使用されます。ボルン項は、溶液中のイオン間の静電相互作用を考慮するための余剰ヘルムホルツエネルギーを与えます。

## 参考文献

1. Born, M. (1920). Z. Phys. 1, 45.
