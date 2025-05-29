```
quadratic_lattice(K::Field ; gram::MatElem) -> Union{ZZLat, QuadLat}
```

Given a matrix `gram` and a field `K`, return the free quadratic lattice inside the quadratic space over `K` with Gram matrix `gram`.

If $K = \mathbb{Q}$, then the output lattice is of type `ZZLat`, seen as a lattice over the ring $\mathbb{Z}$.
