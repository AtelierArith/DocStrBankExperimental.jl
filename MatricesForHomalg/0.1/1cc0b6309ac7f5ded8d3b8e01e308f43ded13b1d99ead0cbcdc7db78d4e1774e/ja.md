```
ConvertMatrixToRow(mat)
```

行ごとに行列 M を展開して1行にします。

```jldoctest
julia> mat = HomalgMatrix(2:7, 3, 2, ZZ)
[2   3]
[4   5]
[6   7]

julia> ConvertMatrixToRow(mat)
[2   3   4   5   6   7]

```
