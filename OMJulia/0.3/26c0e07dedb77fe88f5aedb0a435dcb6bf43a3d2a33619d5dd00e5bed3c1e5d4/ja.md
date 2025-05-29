```
getQuantities(omc, name=nothing)
```

XMLファイルから解析されたすべての変数のリストを返します。

## 引数

  * `omc::OMCSession`:        OpenModelicaコンパイラセッション。
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`: XMLファイルから読み取る変数の名前。                                                                      何も指定しない場合はすべての変数を読み取ります。

関連情報は[`showQuantities`](@ref)を参照してください。
