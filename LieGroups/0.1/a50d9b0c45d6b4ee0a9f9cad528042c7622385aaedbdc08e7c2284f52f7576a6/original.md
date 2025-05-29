```
exp(G::LieGroup{𝔽,AdditionGroupOperation}, X)
exp!(G::LieGroup{𝔽,AdditionGroupOperation}, g, X)
```

Compute the Lie group exponential on a [`LieGroup`](@ref) with an [`AdditionGroupOperation`](@ref). This can be computed in-place of `g`.

Since `e` is just the zero-element with respect to the corresponding `+`, the formula reads $g=0+X=X$.
