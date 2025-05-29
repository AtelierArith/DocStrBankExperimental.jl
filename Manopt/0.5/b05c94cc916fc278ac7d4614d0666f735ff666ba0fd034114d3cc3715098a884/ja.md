```
get_projected_point(amp::AbstractManoptProblem, p)
get_projected_point!(amp::AbstractManoptProblem, q, p)
get_projected_point(M::AbstractManifold, cso::ManifoldConstrainedSetObjective, p)
get_projected_point!(M::AbstractManifold, q, cso::ManifoldConstrainedSetObjective, p)
```

`p`を[`ManifoldConstrainedSetObjective`](@ref)内に保存されている射影を使って射影します。これは`q`のインプレースで行うことができます。
