```
propertyvalues(x)
```

`x`のプロパティの値を反復処理します。

```jldoctest
julia> collect(propertyvalues(1 + 2im))
2-element Vector{Any}:
 1
 2
```
