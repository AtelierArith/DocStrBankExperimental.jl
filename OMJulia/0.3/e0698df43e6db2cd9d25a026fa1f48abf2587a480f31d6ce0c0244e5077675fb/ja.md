```
showQuantities(omc, name=nothing)
```

XMLファイルから解析されたすべての変数の`DataFrame`を返します。

## 引数

  * `omc::OMCSession`:        OpenModelicaコンパイラセッション。
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`:     XMLファイルから読み取る変数の名前。                                                                      何も指定しない場合はすべての変数を読み取ります。

[`getQuantities`](@ref)も参照してください。
