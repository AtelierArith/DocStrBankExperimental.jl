```
FirstZeroRow(mat)
```

最初のゼロ行の正の整数を返します。

```jldoctest
julia> mat = HomalgMatrix(4:9, 3, 2, ZZ)
[4   5]
[6   7]
[8   9]

julia> FirstZeroRow(mat)
4

julia> mat = HomalgMatrix([0, 2, 6, 0, 0, 0], 3, 2, ZZ)
[0   2]
[6   0]
[0   0]

julia> FirstZeroRow(mat)
3

julia> mat = HomalgMatrix([0, 0, 6, 0, 0, 0], 3, 2, ZZ)
[0   0]
[6   0]
[0   0]

julia> FirstZeroRow(mat)
1
```
