```
diff_left_compose(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, g, h, X)
diff_left_compose!(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, Y, g, h, X)
```

Compute the differential of the left group multiplication $λ_g(h) = g∘h$.

Due to differences in the representation of some abelian Lie groups, this method wraps a concrete implementation of a specific abelian LieGroup with inputs of type `AbstractArray{<:Any,0}` and supports in-place computation.

This can be computed in-place of `Y` if `Y` is `mutable`.    
