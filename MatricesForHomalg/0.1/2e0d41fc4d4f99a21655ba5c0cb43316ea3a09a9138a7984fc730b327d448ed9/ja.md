```
HomalgMatrix(L, r, c, R)
```

リング R 上にエントリのリスト L を持つ (r x c)-行列を構築します。

```jldoctest
julia> mat1 = HomalgMatrix([1,2,3,4,5,6], 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> mat2 = HomalgMatrix([[1,2,3],[4,5,6]], 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> mat1 == mat2
true
```
