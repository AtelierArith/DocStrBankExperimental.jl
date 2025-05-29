```
conjugate(CircleGroup, g, h)
conjugate!(CircleGroup, k, g, h)
```

Compute the conjugation map $c_g: \mathcal G → \mathcal G$ given by $c_g(h) = g∘h∘g^{-1} = h$. It simplifies to the identity since the group operation on the circle group is abelian.

This can be computed in-place of `k` if `k` is `mutable`.
