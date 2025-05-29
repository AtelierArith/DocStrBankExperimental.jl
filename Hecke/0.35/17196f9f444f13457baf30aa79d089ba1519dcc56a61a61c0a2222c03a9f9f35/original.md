```
quadratic_lattice(K::Field, B::PMat ; gram = nothing,
                                      check:::Bool = true) -> QuadLat
```

Given a pseudo-matrix `B` with entries in a field `K` return the quadratic lattice spanned by the pseudo-matrix `B` inside the quadratic space over `K` with Gram matrix `gram`.

If `gram` is not supplied, the Gram matrix of the ambient space will be the identity matrix over `K` of size the number of columns of `B`.

By default, `B` is checked to be of full rank. This test can be disabled by setting `check` to false.
