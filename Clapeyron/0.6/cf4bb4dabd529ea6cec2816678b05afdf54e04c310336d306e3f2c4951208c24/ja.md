```
ConstRSP(solvents::Array{String,1},
    ions::Array{String,1};
    userlocations::Vector{String}=[],
    value::Float64 = 78.38484961,
    verbose::Bool=false)

ConstRSP(val::Float64)
```

## 入力パラメータ

  * `value::Float64`: 定数相対静的誘電率 `[-]`

## 説明

この関数は、`value` によって与えられる定数相対静的誘電率モデルを作成するために使用されます。
