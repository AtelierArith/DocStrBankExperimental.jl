```
chunkmask(n, b)
```

A mask to evenly divide `n` indices into regions of size `b`. If `m` = chunkmask(b, n)`, then`m[i, j] = b * (j - 1) < i <= b * j`. Note that this specializes for the cleanup case at the end of the range.

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
