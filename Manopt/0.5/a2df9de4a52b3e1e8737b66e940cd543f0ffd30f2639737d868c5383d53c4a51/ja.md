```
X = get_subgradient(M;;AbstractManifold, sgo::ManifoldSubgradientObjective, p)
get_subgradient!(M;;AbstractManifold, X, sgo::ManifoldSubgradientObjective, p)
```

[`ManifoldSubgradientObjective`](@ref) `sgo` の点 `p` における (部分)勾配を評価します。

評価は `!` バリアントのために `X` の場所で行われます。結果は決定論的でない可能性があり、部分微分の *1* 要素が返されます。
