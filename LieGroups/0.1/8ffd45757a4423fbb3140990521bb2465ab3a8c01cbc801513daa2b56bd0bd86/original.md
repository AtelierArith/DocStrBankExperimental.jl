```
diff_conjugate(G::LieGroup{𝔽,AdditionGroupOperation}, g, h, X)
diff_conjugate!(G::LieGroup{𝔽,AdditionGroupOperation}, Y, g, h, X)
```

Compute the differential of the conjutage $c_g(h) = g∘h∘g^{-1} = g+h-g = h$, which simplifies for [`AdditionGroupOperation`](@ref) to $D(c_g(h))[X] = X$.
