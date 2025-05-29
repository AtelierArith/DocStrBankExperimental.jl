```
行列 M を列方向に展開して列にします。

```

jldoctest julia> mat = HomalgMatrix(2:7, 3, 2, ZZ) [2   3] [4   5] [6   7]

julia> ConvertMatrixToColumn(mat) [2] [4] [6] [3] [5] [7]

```
