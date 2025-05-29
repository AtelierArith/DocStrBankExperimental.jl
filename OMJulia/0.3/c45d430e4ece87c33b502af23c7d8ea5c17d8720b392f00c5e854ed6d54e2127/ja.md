```
getInputs(omc, name=nothing)
```

XMLファイルから解析された出力変数を返します。出力変数に開始値がない場合、返される値は `"None"` です。

## 引数

  * `omc::OMCSession`:        OpenModelicaコンパイラセッション。
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`:  XMLファイルから読み取る出力変数の名前。                                                                       何も指定しない場合はすべての出力変数を読み取ります。
