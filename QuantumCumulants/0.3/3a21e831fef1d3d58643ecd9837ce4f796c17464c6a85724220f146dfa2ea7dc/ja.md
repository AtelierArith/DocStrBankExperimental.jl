```
evalME(me::MeanfieldEquations;limits::Dict{SymbolicUtils.BasicSymbolic,Int64}=Dict{SymbolicUtils.BasicSymbolic,Int64}())
```

関数は、与えられた [`MeanfieldEquations`](@ref) エンティティを評価し、インデックスが挿入され、合計が評価された方程式を再び返します。

# 引数

*`me::MeanfieldEquations`: 評価される [`MeanfieldEquations`](@ref) エンティティ。

# オプション引数

*`limits=Dict{SymbolicUtils.BasicSymbolic,Int64}()`: [`Index`](@ref) エンティティが定義されたときに使用される任意の記号的制限を指定するための別の辞書。方程式に合計が含まれている場合、上限が記号によって与えられるため、これを指定する必要があります。
