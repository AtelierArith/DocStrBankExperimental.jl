```
q = get_proximal_map(M::AbstractManifold, mpo::ManifoldProximalMapObjective, λ, p)
get_proximal_map!(M::AbstractManifold, q, mpo::ManifoldProximalMapObjective, λ, p)
q = get_proximal_map(M::AbstractManifold, mpo::ManifoldProximalMapObjective, λ, p, i)
get_proximal_map!(M::AbstractManifold, q, mpo::ManifoldProximalMapObjective, λ, p, i)
```

`p.M`の点`p`における`ManifoldProximalMapObjective p`の（`i`番目の）近接写像をパラメータ$λ>0$で評価します。
