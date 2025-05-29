```
psparse(f,row_partition,col_partition;assembled)
```

初期化関数 `f` と行および列のパーティション `row_partition` と `col_partition` から [`PSparseMatrix`](@ref) のインスタンスを構築します。

これは次のように同等です。

```
matrix_partition = map(f,row_partition,col_partition)
PSparseMatrix(matrix_partition,row_partition,col_partition,assembled)
```
