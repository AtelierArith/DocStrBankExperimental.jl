```
log(G::LieGroup{𝔽,AdditionGroupOperation}, g)
log!(G::LieGroup{𝔽,AdditionGroupOperation}, X, g)
```

Compute the Lie group logarithm on a [`LieGroup`](@ref) with an [`AdditionGroupOperation`](@ref). This can be computed in-place of `X`.

Since `e` is just the zero-element with respect to the corresponding `+`, the formula reads $X=g-0=g$.
