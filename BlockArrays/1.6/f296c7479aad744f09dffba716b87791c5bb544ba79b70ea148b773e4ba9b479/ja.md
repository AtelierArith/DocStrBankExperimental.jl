```
BlockIndex{N}
```

`BlockIndex`は、ブロックとブロック内のオフセットインデックスの2つの部分でグローバルインデックスを格納するインデックスです。

これは、次のように`BlockArrays`にインデックスを付けるために使用できます：

```jldoctest
julia> arr = Array(reshape(1:25, (5,5)));

julia> a = BlockedArray(arr, [3,2], [1,4])
2×2-blocked 5×5 BlockedMatrix{Int64}:
 1  │   6  11  16  21
 2  │   7  12  17  22
 3  │   8  13  18  23
 ───┼────────────────
 4  │   9  14  19  24
 5  │  10  15  20  25

julia> a[BlockIndex((1,2), (1,2))]
11

julia> a[BlockIndex((2,2), (2,3))]
20
```
