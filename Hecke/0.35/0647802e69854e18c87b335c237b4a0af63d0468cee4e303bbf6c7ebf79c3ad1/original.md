```
hermitian_lattice(E::NumField, gens::Vector ; gram = nothing) -> HermLat
```

Given a list of vectors `gens` and a number field `E` of degree 2, return the hermitian lattice spanned by the elements of `gens` inside the hermitian space over `E` with Gram matrix `gram`.

If `gram` is not supplied, the Gram matrix of the ambient space will be the identity matrix over `E` of size the length of the elements of `gens`.

If `gens` is empty, `gram` must be supplied and the function returns the zero lattice in the hermitan space over `E` with Gram matrix `gram`.
