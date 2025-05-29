```
setInputs(omc, name)
```

入力変数の新しい値を設定します。

## 引数

  * `omc::OMCSession`: OpenModelicaコンパイラセッション。
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}}`:  文字列 "Name=value" またはベクトルの文字列 ["Name1=value1","Name2=value2","Name3=value3"]
