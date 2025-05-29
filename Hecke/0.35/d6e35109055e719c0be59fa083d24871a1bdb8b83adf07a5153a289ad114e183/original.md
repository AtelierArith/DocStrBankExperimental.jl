```
quadratic_lattice(K::Field, gens::Vector ; gram = nothing) -> Union{ZZLat, QuadLat}
```

Given a list of vectors `gens` and a field `K`, return the quadratic lattice spanned by the elements of `gens` inside the quadratic space over `K` with Gram matrix `gram`.

If `gram` is not supplied, the Gram matrix of the ambient space will be the identity matrix over `K` of size the length of the elements of `gens`.

If `gens` is empty, `gram` must be supplied and the function returns the zero lattice in the quadratic space over `K` with gram matrix `gram`.

If $K = \mathbb{Q}$, then the output lattice is of type `ZZLat`, seen as a lattice over the ring $\mathbb{Z}$.
