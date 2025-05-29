```
minors_iterator(A::MatElem, k::Int)
```

行列 `A` の `k`-小行列を計算するイテレータを返します。

# 例

```jldoctest
julia> A = ZZ[1 2 3; 4 5 6]
[1   2   3]
[4   5   6]

julia> first(minors_iterator(A, 2))
-3

julia> collect(minors_iterator(A, 2))
3-element Vector{BigInt}:
 -3
 -6
 -3

```
