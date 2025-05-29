```
getParameters(omc, name=nothing)
```

XMLファイルから解析されたパラメータ変数を返します。

## 引数

  * `omc::OMCSession`:        OpenModelicaコンパイラセッション。
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`:     XMLファイルから読み取るパラメータの名前。                                                                      何も指定しない場合はすべてのパラメータを読み取ります。
