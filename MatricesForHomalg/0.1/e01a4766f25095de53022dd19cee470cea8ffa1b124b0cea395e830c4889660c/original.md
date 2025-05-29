```
HomalgRing(mat)
```

Return the ring underlying the matrix mat.

```jldoctest
julia> mat = HomalgMatrix(1:6, 2, 3, ZZ)
[1   2   3]
[4   5   6]

julia> HomalgRing(mat)
Integer ring

julia> mat = HomalgMatrix(1:6, 2, 3, QQ)
[1   2   3]
[4   5   6]

julia> HomalgRing(mat)
Rational field
```
