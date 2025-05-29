```
inv(G::LieGroup{𝔽,AdditionGroupOperation}, g)
inv!(G::LieGroup{𝔽,AdditionGroupOperation}, h, g)
```

Compute the inverse group element $g^{-1}$, which for the [`AdditionGroupOperation`](@ref) simplifies to $-g$. This can be done in-place of `h`.
