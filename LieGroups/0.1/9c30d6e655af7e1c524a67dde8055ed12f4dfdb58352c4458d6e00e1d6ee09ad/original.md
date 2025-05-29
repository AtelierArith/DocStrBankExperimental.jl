```
compose(G::LieGroup{𝔽,AdditionGroupOperation}, g, h)
compose!(G::LieGroup{𝔽,AdditionGroupOperation}, k, g, h)
```

Compute the group operation composition of `g` and `h` with respect to the [`AdditionGroupOperation`](@ref) on `G`, which falls back to calling `g+h`, where `+` is assumed to be overloaded accordingly.

This can be computed in-place of `k`.
