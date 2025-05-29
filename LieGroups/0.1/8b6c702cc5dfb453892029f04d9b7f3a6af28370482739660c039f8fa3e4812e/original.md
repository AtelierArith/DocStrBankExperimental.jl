```
diff_inv(G::LieGroup{𝔽,AdditionGroupOperation}, g, X)
diff_inv!(G::LieGroup{𝔽,AdditionGroupOperation}, Y, g, X)
```

Compute the differential of the inverse operation $ι_{\mathcal G}(g) = g^-1 = -g$, which simplifies for [`AdditionGroupOperation`](@ref) to $Dι_{\mathcal G}(g)[X] = -X$
