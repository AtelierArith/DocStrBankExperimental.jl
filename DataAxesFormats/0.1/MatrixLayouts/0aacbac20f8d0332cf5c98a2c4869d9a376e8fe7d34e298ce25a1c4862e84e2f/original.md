```
@assert_matrix(matrix::Any, [n_rows::Integer, n_columns::Integer], [major_axis::Int8])
```

Assert that the `matrix` is an `AbstractMatrix` and optionally that it has `n_rows` and `n_columns`. If the `major_axis` is given, also calls `check_efficient_action` to verify that the matrix is in an efficient layout.
