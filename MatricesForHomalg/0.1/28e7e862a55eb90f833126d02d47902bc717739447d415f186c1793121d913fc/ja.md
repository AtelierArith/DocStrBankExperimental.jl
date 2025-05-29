```
IsEmptyMatrix(mat)
```

matにエントリが含まれていない場合はtrueを返し、それ以外の場合はfalseを返します。

```jldoctest
julia> mat = HomalgMatrix([], 0, 0, ZZ)
0 by 0 empty matrix

julia> IsEmptyMatrix(mat)
true
```
