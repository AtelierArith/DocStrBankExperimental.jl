```
diff_inv(G::AbstractLieGroup, g, X)
diff_inv!(G::AbstractLieGroup, Y, g, X)
```

Compute the differential of the function $ι_{\mathcal G}(g) = g^{-1}$, where $Dι_{\mathcal G}(g): \mathfrak g → \mathfrak g$. This can be done in-place of `Y`.
