```
splitmask(n, P)
```

`n` インデックスを P 領域に均等に分割するためのマスク。もし `M = splitmask(P, n)` ならば、`M[i, j] = fld(n * (j - 1), P) <= i < fld(n * j, P)` です。

```jldoctest
julia> splitmask(10, 3)
10×3 Finch.SplitMask{Int64}:
 1  0  0
 1  0  0
 1  0  0
 0  1  0
 0  1  0
 0  1  0
 0  0  1
 0  0  1
 0  0  1
 0  0  1

```
