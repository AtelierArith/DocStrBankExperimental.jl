```
q = get_proximal_map(M::AbstractManifold, mpo::ManifoldProximalMapObjective, λ, p)
get_proximal_map!(M::AbstractManifold, q, mpo::ManifoldProximalMapObjective, λ, p)
q = get_proximal_map(M::AbstractManifold, mpo::ManifoldProximalMapObjective, λ, p, i)
get_proximal_map!(M::AbstractManifold, q, mpo::ManifoldProximalMapObjective, λ, p, i)
```

evaluate the (`i`th) proximal map of `ManifoldProximalMapObjective p` at the point `p` of `p.M` with parameter $λ>0$.
