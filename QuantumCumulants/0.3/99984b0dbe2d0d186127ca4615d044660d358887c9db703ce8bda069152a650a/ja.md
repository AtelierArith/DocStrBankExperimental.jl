```
evaluate(eqs::IndexedMeanfieldEquations;limits)
evaluate(corr::CorrelationFunction;limits)
evaluate(x;limits)
```

指定された [`MeanfieldEquations`](@ref) エンティティを評価し、インデックスが挿入され、合計が評価された方程式を再び返す関数です。個々の項や [`CorrelationFunction`](@ref) エンティティに対しても呼び出すことができ、これらの項内の任意の合計を評価します。

# 引数

*`me::MeanfieldEquations`: 評価される [`MeanfieldEquations`](@ref) エンティティ。

# オプション引数

*`limits::Dict{BasicSymbolic,Int64}=Dict{Symbol,Int64}()`: [`Index`](@ref) エンティティが定義されたときに使用される任意の記号的制限を指定するための別の辞書。この辞書は、方程式に記号によって上限が与えられる合計が含まれている場合に指定する必要があります。*`h`: 評価される特定のヒルベルト空間を指定するヒルベルト空間、ヒルベルト空間のベクトル、または数値。指定されたもの以外の他のヒルベルト空間は評価しません。
