```
RefinementMatrix(m, n, row_pointer, column_start, nzval)
```

The refinement matrix is a sparse matrix encoding for matrices which:

1. Have consecutive non-zeros in all rows and columns
2. Have at least 1 nonzero in every row and column

The non-zeros are stored in a dense vector per row.

## Fields

  * `m`: The number of rows of the matrix
  * `n`: The number of columns of the matrix
  * `row_pointer`: `row_pointer[i]` indicates where in `nzval` the data for the `i`-th row starts
  * `column_start`: `column_start[i]` indicates at which column the first nonzero for the `i`-th row is
  * `nzval`: The nonzero values in the matrix
