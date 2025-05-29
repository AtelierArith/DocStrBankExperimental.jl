```
RowReducedEchelonForm(mat)
```

行基本形と行列 mat のランクを返します。

```jldoctest julia> mat = HomalgMatrix(reverse(1:9), 3, 3, ZZ) [9   8   7] [6   5   4] [3   2   1]

julia> RowReducedEchelonForm(mat) ([3 0 -3; 0 1 2; 0 0 0], 2)

julia> mat = HomalgMatrix(reverse(1:9), 3, 3, QQ) [9   8   7] [6   5   4] [3   2   1]

julia> RowReducedEchelonForm(mat) ([1 0 -1; 0 1 2; 0 0 0], 2)
```
