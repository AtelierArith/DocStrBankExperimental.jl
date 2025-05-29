```
X = get_subtrahend_gradient(M::AbstractManifold, dcpo::ManifoldDifferenceOfConvexProximalObjective, p)
get_subtrahend_gradient!(M::AbstractManifold, X, dcpo::ManifoldDifferenceOfConvexProximalObjective, p)
```

点`p`における[`ManifoldDifferenceOfConvexProximalObjective`](@ref)のサブトラヘンド$h$の勾配を評価します（Xの代わりに）。
