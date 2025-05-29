```
scale(me::IndexedMeanfieldEquations;h)
scale(me::CorrelationFunction;h)
```

関数は、与えられた [`MeanfieldEquations`](@ref) または [`CorrelationFunction`](@ref) エンティティを評価し、インデックスが挿入され、和が評価された方程式を再び返します。これは、[`ClusterSpace`](@ref) を使用して計算する際に行われるのと同じ関係に関して行われます。このため、与えられた（サブ）システム内のすべてのエンティティがシステムに対して同等に作用していると考えられます。

# 引数

*`me::IndexedMeanfieldEquations`: スケーリングされるべき [`MeanfieldEquations`](@ref) エンティティ。

# オプション引数

*`h`: スケーリングされる特定のヒルベルト空間を指定するヒルベルト空間、ヒルベルト空間のベクトル、または数値。与えられたもの以外の他のヒルベルト空間はスケーリングされません。
