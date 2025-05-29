```
matrix_blocked_df(A, row_nfreedofs, col_nfreedofs = row_nfreedofs)
```

Extract the "data-free" partition of a matrix.

The matrix is assumed to be composed of four blocks

```
A = [A_ff A_fd
     A_df A_dd]
```

Here `f` stands for free, and `d` stands for data (i.e. fixed, prescribed, ...). The size of the `ff` block is `row_nfreedofs, col_nfreedofs`. Neither one of the blocks is square, unless `row_nfreedofs == col_nfreedofs`.

When `row_nfreedofs == col_nfreedofs`, only the number of rows needs to be given.
