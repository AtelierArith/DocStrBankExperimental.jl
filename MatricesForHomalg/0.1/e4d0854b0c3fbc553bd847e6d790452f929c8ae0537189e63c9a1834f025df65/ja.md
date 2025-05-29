```
RowRankOfMatrix(mat)
```

行列 mat の行ランクを非負整数として返します。

```jldoctest
julia> mat1 = HomalgMatrix(4:9, 3, 2, ZZ)
[4   5]
[6   7]
[8   9]

julia> RowRankOfMatrix(mat1)
2

julia> mat2 = HomalgIdentityMatrix(3, ZZ)
[1   0   0]
[0   1   0]
[0   0   1]

julia> RowRankOfMatrix(mat2)
3
```
