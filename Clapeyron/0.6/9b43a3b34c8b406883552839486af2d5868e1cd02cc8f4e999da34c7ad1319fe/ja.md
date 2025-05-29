```
Schreckenberg(solvents::Array{String,1},
     ions::Array{String,1};
     userlocations::Vector{String}=[],
     verbose::Bool=false)
```

## 入力パラメータ

  * `d_T::Float64`: 単一パラメータ - 温度依存の誘電率 `[-]`
  * `d_V::Float64`: 単一パラメータ - 体積依存の誘電率 `[-]`
  * `charge::Float64`: 単一パラメータ - 電荷 `[-]`

## 説明

この関数はシュレッケンベルグモデルを作成するために使用されます。シュレッケンベルグ項は溶媒の混合物に対する誘電率を推定します。

## 参考文献

1. Schreckenberg, J., Dufal, S., Haslam, A.J., Adjiman, C.S., Jackson, G., Galindo, A. (2014). Modelling of the thermodynamic and solvation properties of electrolyte solutions with the statistical associating fluid theory for potentials of variable range. Molecular Physics, 112(17), 2339-2364.
