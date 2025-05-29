```
FirstZeroColumn(mat)
```

最初のゼロ列の正の整数を返します。

```jldoctest
julia> mat = HomalgMatrix(4:9, 2, 3, ZZ)
[4   5   6]
[7   8   9]

julia> FirstZeroColumn(mat)
4

julia> mat = HomalgMatrix([0, 2, 0, 0, 0, 0], 2, 3, ZZ)
[0   2   0]
[0   0   0]

julia> FirstZeroColumn(mat)
1

julia> mat = HomalgZeroMatrix(3,3,ZZ)
[0   0   0]
[0   0   0]
[0   0   0]

julia> FirstZeroColumn(mat)
1
```
