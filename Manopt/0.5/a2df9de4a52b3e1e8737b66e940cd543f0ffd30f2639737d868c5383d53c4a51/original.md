```
X = get_subgradient(M;;AbstractManifold, sgo::ManifoldSubgradientObjective, p)
get_subgradient!(M;;AbstractManifold, X, sgo::ManifoldSubgradientObjective, p)
```

Evaluate the (sub)gradient of a [`ManifoldSubgradientObjective`](@ref) `sgo` at the point `p`.

The evaluation is done in place of `X` for the `!`-variant. The result might not be deterministic, *one* element of the subdifferential is returned.
