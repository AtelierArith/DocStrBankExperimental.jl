```julia
struct LinearRelative{N, T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

2つのスカラー変数間のデフォルトの線形オフセット。

$$
X_2 = X_1 + η_Z
$$
