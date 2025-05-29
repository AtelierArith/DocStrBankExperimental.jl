```
BlockIndex{N}
```

A `BlockIndex` is an index which stores a global index in two parts: the block and the offset index into the block.

It can be used to index into `BlockArrays` in the following manner:

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
