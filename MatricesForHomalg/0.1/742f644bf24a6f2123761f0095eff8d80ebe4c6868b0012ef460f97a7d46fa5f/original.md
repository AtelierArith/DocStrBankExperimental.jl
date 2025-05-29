```
StringDisplay(mat)
```

Returns the matrix mat as a string.

```jldoctest
julia> mat = HomalgMatrix(4:9, 3, 2, ZZ)
[4   5]
[6   7]
[8   9]

julia> StringDisplay(mat)
"[4 5; 6 7; 8 9]"
```
