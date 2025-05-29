```
X = get_subgradient(M::AbstractManifold, sgo::AbstractManifoldGradientObjective, p)
get_subgradient!(M::AbstractManifold, X, sgo::AbstractManifoldGradientObjective, p)
```

Evaluate the subgradient, which for the case of a objective having a gradient, means evaluating the gradient itself.

While in general, the result might not be deterministic, for this case it is.
