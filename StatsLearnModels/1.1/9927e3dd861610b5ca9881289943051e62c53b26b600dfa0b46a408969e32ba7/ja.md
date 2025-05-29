```
KNNClassifier(k, metric=Euclidean(); leafsize=10, reorder=true)
```

`k`近傍法分類モデルで、`metric`はDistances.jlからのものです。オプションで、[NearestNeighbors.jl](https://github.com/KristofferC/NearestNeighbors.jl)の基盤となる木に対して`leafsize`と`reorder`オプションを指定できます。

また、[`KNNRegressor`](@ref)も参照してください。
