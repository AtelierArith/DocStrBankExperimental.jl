```julia
updateindex!(ext, op, v, i, j)

```

行列の要素を操作 `op` で更新します。これは以下のコードを置き換え、アクセス中に1回のインデックス検索を節約できます：

```@example
using ExtendableSparse # hide
A=ExtendableSparseMatrix(3,3)
A[1,2]+=0.1
A
```

```@example
using ExtendableSparse # hide

A=ExtendableSparseMatrix(3,3)
updateindex!(A,+,0.1,1,2)
A
```

もし `v` がゼロであれば、新しいエントリは作成されません。
