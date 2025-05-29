```
getLinearizationOptions(omc, name=nothing)
```

線形化オプションを返します。

## 引数

  * `omc::OMCSession`:        OpenModelicaコンパイラセッション。
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`: 線形化オプションの名前。                                                                      何も提供されない場合は、すべての線形化オプションを返します。
