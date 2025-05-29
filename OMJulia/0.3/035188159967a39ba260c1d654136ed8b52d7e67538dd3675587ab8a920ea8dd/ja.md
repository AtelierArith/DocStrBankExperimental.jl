```
setSimulationOptions(omc, name)
```

シミュレーションオプションの値を `stopTime` や `stepSize` のように設定します。

## 引数

  * `omc::OMCSession`: OpenModelica コンパイラセッション。
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}}`:  文字列 "Name=value" またはベクトルの文字列 ["Name1=value1","Name2=value2","Name3=value3"]
