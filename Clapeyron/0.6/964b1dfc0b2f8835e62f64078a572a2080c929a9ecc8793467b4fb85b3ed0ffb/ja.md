```
LinMixRSP(solvents::Array{String,1},
     ions::Array{String,1};
     userlocations::Vector{String}=[],
     verbose::Bool=false)
```

## 入力パラメータ

  * `dielectric_constant::Float64`: 定数相対静的誘電率 `[-]`

## 説明

この関数は、各溶媒が `dielectric_constant` を持つ溶媒の混合物に対して、線形混合則相対静的誘電率モデルを作成するために使用されます。
