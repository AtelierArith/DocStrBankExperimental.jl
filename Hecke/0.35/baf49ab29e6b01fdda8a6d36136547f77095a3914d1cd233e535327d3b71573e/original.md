```
hermitian_lattice(E::NumField, basis::MatElem; gram = nothing,
			                    check::Bool = true) -> HermLat
```

Given a matrix `basis` and a number field `E` of degree 2, return the hermitian lattice spanned by the rows of `basis` inside the hermitian space over `E` with Gram matrix `gram`.

If `gram` is not supplied, the Gram matrix of the ambient space will be the identity matrix over `E` of size the number of columns of `basis`.

By default, `basis` is checked to be of full rank. This test can be disabled by setting `check` to false.
