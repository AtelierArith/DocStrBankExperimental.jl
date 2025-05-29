```
fieldvalues(x)
```

`x`のフィールドの値を反復処理します。

```jldoctest
julia> collect(fieldvalues(1 + 2im))
2-element Vector{Any}:
 1
 2
```
