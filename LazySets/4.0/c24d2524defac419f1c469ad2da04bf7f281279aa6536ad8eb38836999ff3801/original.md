```
get_row(spmexp::SparseMatrixExp{N}, i::Int;
        [backend]=get_exponential_backend()) where {N}
```

Return a single row of a sparse matrix exponential.

### Input

  * `spmexp`  – sparse matrix exponential
  * `i`       – row index
  * `backend` – (optional; default: `get_exponential_backend()`) exponentiation              backend

### Output

A row vector corresponding to the `i`th row of the matrix exponential.

### Notes

This implementation uses Julia's `transpose` function to create the result. The result is of type `Transpose`; in Julia versions older than v0.7, the result was of type `RowVector`.
