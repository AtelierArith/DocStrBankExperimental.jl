```
diff_right_compose(G::LieGroup{𝔽,AdditionGroupOperation}, h, g, X)
diff_right_compose!(G::LieGroup{𝔽,AdditionGroupOperation}, Y, h, g, X)
```

Compute the differential of the right group multiplication $ρ_g(h) = h∘g$, which simplifies for [`AdditionGroupOperation`](@ref) to $Dρ_g(h)[X] = X$.
