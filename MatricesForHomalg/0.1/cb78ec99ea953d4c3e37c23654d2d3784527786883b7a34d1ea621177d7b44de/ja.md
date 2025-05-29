```
IsSymmetricMatrix(mat)
```

行列 mat が主対角線に関して対称であれば true を返し、そうでなければ false を返します。

```jldoctest
julia> mat = HomalgMatrix([1,2,3,2,4,5,3,5,6], 3, 3, ZZ)
[1   2   3]
[2   4   5]
[3   5   6]

julia> IsSymmetricMatrix(mat)
true
```
