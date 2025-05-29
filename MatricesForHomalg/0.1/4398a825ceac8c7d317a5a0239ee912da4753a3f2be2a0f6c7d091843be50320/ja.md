```
IsZero(mat)
```

matがゼロ行列であればtrueを返し、そうでなければfalseを返します。

```jldoctest
julia> mat = HomalgZeroMatrix(3, 2, ZZ)
[0   0]
[0   0]
[0   0]

julia> IsZero(mat)
true
```
