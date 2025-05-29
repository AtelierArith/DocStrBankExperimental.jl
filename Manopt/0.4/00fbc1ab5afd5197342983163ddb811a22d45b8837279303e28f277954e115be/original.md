```
X = get_subtrahend_gradient(M::AbstractManifold, dcpo::ManifoldDifferenceOfConvexProximalObjective, p)
get_subtrahend_gradient!(M::AbstractManifold, X, dcpo::ManifoldDifferenceOfConvexProximalObjective, p)
```

Evaluate the gradient of the subtrahend $h$ from within a [`ManifoldDifferenceOfConvexProximalObjective`](@ref)``P`at the point`p` (in place of X).
