```
getContinuous(omc, name=nothing)
```

XMLファイルから解析された連続変数を返します。

## 引数

  * `omc::OMCSession`:        OpenModelicaコンパイラセッション。
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`:  XMLファイルから読み取る連続変数の名前。                                                                       何も指定しない場合はすべての連続変数を読み取ります。
