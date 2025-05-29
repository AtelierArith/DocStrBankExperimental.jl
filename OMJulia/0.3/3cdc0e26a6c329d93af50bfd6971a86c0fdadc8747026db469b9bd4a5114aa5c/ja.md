```
getSolutions(omc::OMCSession, name=nothing; resultfile=nothing)
```

結果ファイルを読み込み、シミュレーション結果を返します

## 引数

  * `omc::OMCSession`:        OpenModelicaコンパイラセッション。
  * `name::Union{<:AbstractString, Array{<:AbstractString,1}, Nothing}`:  結果ファイルから読み取る変数の名前。                                                                       何も指定しない場合はすべての変数を読み取ります。

## キーワード引数

  * `resultfile::Union{AbstractString, Nothing}`:     結果ファイルへのパス。何も指定しない場合は保存された結果ファイルを使用します。
