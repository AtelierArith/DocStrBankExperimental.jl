```
splitmask(n, P)
```

A mask to evenly divide `n` indices into P regions. If `M = splitmask(P, n)`, then `M[i, j] = fld(n * (j - 1), P) <= i < fld(n * j, P)`.

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
