```
psparse(f,row_partition,col_partition;assembled)
```

Build an instance of [`PSparseMatrix`](@ref) from the initialization function `f` and the partition for rows and columns `row_partition` and `col_partition`.

Equivalent to

```
matrix_partition = map(f,row_partition,col_partition)
PSparseMatrix(matrix_partition,row_partition,col_partition,assembled)
```
