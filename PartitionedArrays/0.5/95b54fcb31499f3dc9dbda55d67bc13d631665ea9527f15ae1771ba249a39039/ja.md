```
psparse([f,]I,J,V,row_partition,col_partition;kwargs...) -> Task
```

[`PSparseMatrix`](@ref) のインスタンスを、基になる各部分から任意のエントリを設定することによって作成します。これは、セットアップに必要な通信を行いながらレイテンシを隠すことを可能にする [`PSparseMatrix`](@ref) のインスタンスを生成するタスクを返します。
