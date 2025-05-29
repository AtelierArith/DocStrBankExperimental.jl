```
scaleME(me::IndexedMeanfieldEquations)
```

関数で、与えられた [`MeanfieldEquations`](@ref) エンティティを評価し、インデックスが挿入され、合計が評価された方程式を再び返します。これは、[`ClusterSpace`](@ref) を使用して演算子で計算する際に行われるのと同じ関係に関して行われます。

# 引数

*`me::MeanfieldEquations`: 評価されるべき [`MeanfieldEquations`](@ref) エンティティ。
