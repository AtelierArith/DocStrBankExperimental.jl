```
X = get_subtrahend_gradient(M::AbstractManifold, dcpo::ManifoldDifferenceOfConvexProximalObjective, p)
get_subtrahend_gradient!(M::AbstractManifold, X, dcpo::ManifoldDifferenceOfConvexProximalObjective, p)
```

サブトラヘンド $h$ の勾配を、点 `p` での [`ManifoldDifferenceOfConvexProximalObjective`](@ref)``P` から評価します（Xの代わりに）。
