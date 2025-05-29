```
quadratic_lattice(K::Field, basis::MatElem ; gram = nothing,
                                             check::Bool = true)
                                                      -> Union{ZZLat, QuadLat}
```

Given a matrix `basis` and a field `K`, return the quadratic lattice spanned by the rows of `basis` inside the quadratic space over `K` with Gram matrix `gram`.

If `gram` is not supplied, the Gram matrix of the ambient space will be the identity matrix over `K` of size the number of columns of `basis`.

By default, `basis` is checked to be of full rank. This test can be disabled by setting `check` to false.

If $K = \mathbb{Q}$, then the output lattice is of type `ZZLat`, seen as a lattice over the ring $\mathbb{Z}$.
