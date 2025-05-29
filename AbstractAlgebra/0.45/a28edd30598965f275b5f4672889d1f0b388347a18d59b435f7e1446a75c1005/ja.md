```
minors_with_position(A::MatElem, k::Int)
```

`A`の`k`-小行列と、関与する行と列に関するデータを含む配列を返します。

# 例

```jldoctest
julia> A = ZZ[1 2 3; 4 5 6]
[1   2   3]
[4   5   6]

julia> minors_with_position(A, 2)
3-element Vector{Tuple{BigInt, Vector{Int64}, Vector{Int64}}}:
 (-3, [1, 2], [1, 2])
 (-6, [1, 2], [1, 3])
 (-3, [1, 2], [2, 3])

```
