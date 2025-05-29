```
KNNRegressor(k, metric=Euclidean(); leafsize=10, reorder=true)
```

`k`近傍回帰モデルで、`metric`はDistances.jlからのものです。オプションで、[NearestNeighbors.jl](https://github.com/KristofferC/NearestNeighbors.jl)の基盤となる木のために`leafsize`と`reorder`オプションを指定できます。

また、[`KNNClassifier`](@ref)も参照してください。
