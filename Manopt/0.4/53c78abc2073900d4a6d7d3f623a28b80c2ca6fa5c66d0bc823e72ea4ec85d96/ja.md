```
q = get_proximal_map(M::AbstractManifold, mpo::ManifoldProximalMapObjective, λ, p)
get_proximal_map!(M::AbstractManifold, q, mpo::ManifoldProximalMapObjective, λ, p)
q = get_proximal_map(M::AbstractManifold, mpo::ManifoldProximalMapObjective, λ, p, i)
get_proximal_map!(M::AbstractManifold, q, mpo::ManifoldProximalMapObjective, λ, p, i)
```

`ManifoldProximalMapObjective p`の点`p`における（`i`番目の）近接マップをパラメータ$λ>0$で評価します。
