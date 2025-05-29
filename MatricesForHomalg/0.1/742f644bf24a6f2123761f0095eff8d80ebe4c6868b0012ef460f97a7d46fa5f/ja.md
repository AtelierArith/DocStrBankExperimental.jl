```
StringDisplay(mat)
```

行列 mat を文字列として返します。

```jldoctest
julia> mat = HomalgMatrix(4:9, 3, 2, ZZ)
[4   5]
[6   7]
[8   9]

julia> StringDisplay(mat)
"[4 5; 6 7; 8 9]"
```
