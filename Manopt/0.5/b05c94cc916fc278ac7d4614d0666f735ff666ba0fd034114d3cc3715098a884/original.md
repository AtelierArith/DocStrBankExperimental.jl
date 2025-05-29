```
get_projected_point(amp::AbstractManoptProblem, p)
get_projected_point!(amp::AbstractManoptProblem, q, p)
get_projected_point(M::AbstractManifold, cso::ManifoldConstrainedSetObjective, p)
get_projected_point!(M::AbstractManifold, q, cso::ManifoldConstrainedSetObjective, p)
```

Project `p` with the projection that is stored within the [`ManifoldConstrainedSetObjective`](@ref). This can be done in-place of `q`.
