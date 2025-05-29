```
setParameters(omc, name; verbose=true)
```

ユーザーによって定義されたパラメータ変数のパラメータ値を設定します

## 引数

  * `omc::OMCSession`: OpenModelicaコンパイラセッション。
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}}`:  文字列 "Name=value" またはベクトルの文字列 ["Name1=value1","Name2=value2","Name3=value3"]

## キーワード引数

  * `verbose::Bool`:     setParametersが失敗した場合に追加情報を表示します。
