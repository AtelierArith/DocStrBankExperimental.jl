```
hermitian_lattice(E::NumField, B::PMat; gram = nothing,
			             check::Bool = true) -> HermLat
```

Given a pseudo-matrix `B` with entries in a number field `E` of degree 2, return the hermitian lattice spanned by the pseudo-matrix `B` inside the hermitian space over `E` with Gram matrix `gram`.

If `gram` is not supplied, the Gram matrix of the ambient space will be the identity matrix over `E` of size the number of columns of `B`.

By default, `B` is checked to be of full rank. This test can be disabled by setting `check` to false.
