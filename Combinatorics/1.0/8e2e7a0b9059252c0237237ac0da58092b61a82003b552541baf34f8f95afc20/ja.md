```
permutations(a, t)
```

インデックス可能なオブジェクト `a` のサイズ `t` のすべての順列を生成します。 `a` の長さが定義されている場合のみ機能します。 `(t <= 0) || (t > length(a))` の場合、`a` のエルタイプの空のベクトルを返します。

# 例

```jldoctest
julia> [ (len, permutations(1:3, len)) for len in -1:4 ]
6-element Vector{Tuple{Int64, Any}}:
 (-1, Vector{Int64}[])
 (0, [Int64[]])
 (1, [[1], [2], [3]])
 (2, Combinatorics.Permutations{UnitRange{Int64}}(1:3, 2))
 (3, Combinatorics.Permutations{UnitRange{Int64}}(1:3, 3))
 (4, Vector{Int64}[])

julia> [ (len, collect(permutations(1:3, len))) for len in -1:4 ]
6-element Vector{Tuple{Int64, Vector{Vector{Int64}}}}:
 (-1, [])
 (0, [[]])
 (1, [[1], [2], [3]])
 (2, [[1, 2], [1, 3], [2, 1], [2, 3], [3, 1], [3, 2]])
 (3, [[1, 2, 3], [1, 3, 2], [2, 1, 3], [2, 3, 1], [3, 1, 2], [3, 2, 1]])
 (4, [])
```
