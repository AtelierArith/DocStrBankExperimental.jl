```
properties(x)
```

`x`のプロパティの名前と値を反復処理します。

```jldoctest
julia> collect(properties(1 + 2im))
2-element Vector{Any}:
 (:re, 1)
 (:im, 2)
```
