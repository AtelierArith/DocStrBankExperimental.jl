```
chunkmask(n, b)
```

`n` インデックスをサイズ `b` の領域に均等に分割するためのマスク。もし `m` = chunkmask(b, n)`なら、`m[i, j] = b * (j - 1) < i <= b * j` となります。これは範囲の最後のクリーンアップケースに特化しています。

```jldoctest
julia> chunkmask(10, 3)
10×4 Finch.ChunkMask{Int64}:
 1  0  0  0
 1  0  0  0
 1  0  0  0
 0  1  0  0
 0  1  0  0
 0  1  0  0
 0  0  1  0
 0  0  1  0
 0  0  1  0
 0  0  0  1

```
