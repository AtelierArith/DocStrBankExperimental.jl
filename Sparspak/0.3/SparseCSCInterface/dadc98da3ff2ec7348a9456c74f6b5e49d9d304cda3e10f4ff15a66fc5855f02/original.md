```
sparspaklu(m::SparseMatrixCSC; factorize=true) -> lu::SparseSolver
```

If `factorize==true`, calculate LU factorization using Sparspak. Steps are `findorder`, `symbolicfactor`, `factor`.

If   `factorize==false`,   ordering,    symbolic   factorization   and factorization are delayed to a subsequent call to `sparspaklu!`.

Returns  a  `SparseSolver` instance in the respective state,  which has methods for `LinearAlgebra.ldiv!` and "backslash".
