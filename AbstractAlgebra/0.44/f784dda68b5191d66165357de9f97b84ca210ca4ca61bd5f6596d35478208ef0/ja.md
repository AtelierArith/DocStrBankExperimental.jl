```
minors(A::MatElem, k::Int)
```

`A`の`k`-小行列からなる配列を返します。

# 例

```jldoctest
julia> A = ZZ[1 2 3; 4 5 6]
[1   2   3]
[4   5   6]

julia> minors(A, 2)
3-element Vector{BigInt}:
 -3
 -6
 -3

```
