```
SupernodalMatrix(
    F::SparseArrays.CHOLMOD.Factor;
    transpose_chunks = false,
    symmetric_access = false,
    depermuted_access = false,
)
```

Construct a `SupernodalMatrix` from a supernodal Cholesky factorization.

Keyword arguments are explained in the `SupernodalMatrix` docstring.
