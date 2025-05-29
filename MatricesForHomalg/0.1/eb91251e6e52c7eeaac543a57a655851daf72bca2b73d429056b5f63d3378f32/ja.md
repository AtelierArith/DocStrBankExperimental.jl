```
IsOne(mat)
```

matが単位行列であればtrueを返し、そうでなければfalseを返します。

```jldoctest
julia> mat = HomalgIdentityMatrix(3, ZZ)
[1   0   0]
[0   1   0]
[0   0   1]

julia> IsOne(mat)
true
```
