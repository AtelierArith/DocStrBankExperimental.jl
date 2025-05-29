```
GCMSABorn(solvents::Array{String,1},
     ions::Array{String,1};
     RSPmodel=ConstRSP,
     SAFTlocations=String[],
     userlocations=String[],
     verbose=false)
```

## 入力パラメータ

  * `sigma`: 単一パラメータ (`Float64`) - ハードスフェア直径 `[m]`
  * `sigma_born`: 単一パラメータ (`Float64`) - ボーン直径 `[m]`
  * `charge`: 単一パラメータ (`Float64`) - 電荷 `[-]`

## 入力モデル

  * `RSPmodel`: 相対静的誘電率モデル

## 説明

この関数は、SAFT-gamma E Mieで使用されるグループ寄与平均球近似-ボーンモデルを作成するために使用されます。
