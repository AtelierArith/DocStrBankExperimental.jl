```
abstract type VarFeature <: AbstractFeature end
```

特徴関数の抽象型で、（多変量）データ上で計算可能です。多変量データセットのインスタンスは、論理的特徴を定義するために使用できる多数の*変数*の値を持っています。

たとえば、次元データ（例：多変量時系列、デジタル画像および動画）では、特徴は特定の区間/長方形/立方体（一般的には[`SoleLogics.GeometricalWorld`](@ref)）における特定の変数の最小値として計算できます。

次元特徴の例として、*min[V1]*を考えてみましょう。これは、特定の世界における変数1の最小値を計算します。`ScalarCondition`のような*min[V1] >= 10*は、したがって、世界で評価できます。

また、[`scalarlogiset`](@ref)、[`featvaltype`](@ref)、[`computefeature`](@ref)、[`SoleLogics.Interval`](@ref)も参照してください。
