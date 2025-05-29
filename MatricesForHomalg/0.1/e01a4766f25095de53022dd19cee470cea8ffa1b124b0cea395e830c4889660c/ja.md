```
HomalgRing(mat)
```

行列 mat の基礎となる環を返します。

```jldoctest
julia> mat = HomalgMatrix(1:6, 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> HomalgRing(mat)
整数環

julia> mat = HomalgMatrix(1:6, 2, 3, QQ)
[1   2   3]
[4   5   6]

julia> HomalgRing(mat)
有理数体
```
