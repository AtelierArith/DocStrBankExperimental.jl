```julia
updateindex!(csc, op, v, i, j)

```

行列の要素を操作 `op` で更新し、新しい非ゼロ要素を導入しません。

これは、次のコードを置き換え、アクセス中にインデックス検索を1回節約できます：

```@example
using ExtendableSparse # hide
using SparseArrays # hide
A=spzeros(3,3)
A[1,2]+=0.1
A
```

```@example
using ExtendableSparse # hide
using SparseArrays # hide
A=spzeros(3,3)
updateindex!(A,+,0.1,1,2)
A
```
