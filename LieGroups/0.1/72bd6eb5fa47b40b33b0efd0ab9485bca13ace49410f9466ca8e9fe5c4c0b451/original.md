```
conjugate(G::AbstractLieGroup, g, h)
conjugate!(G::AbstractLieGroup, k, g, h)
```

Compute the conjugation map $c_g: \mathcal G → \mathcal G$ given by $c_g(h) = g∘h∘g^{-1}$. This can be done in-place of `k`.
