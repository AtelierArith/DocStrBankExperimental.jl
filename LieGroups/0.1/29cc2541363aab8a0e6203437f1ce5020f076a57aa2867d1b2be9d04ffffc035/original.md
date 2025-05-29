```
diff_left_compose(G::LieGroup{𝔽,AdditionGroupOperation}, g, h, X)
diff_left_compose!(G::LieGroup{𝔽,AdditionGroupOperation}, Y, g, h, X)
```

Compute the differential of the left group multiplication $λ_g(h) = g∘h$, which simplifies for [`AdditionGroupOperation`](@ref) to $Dλ_g(h)[X] = X$.
