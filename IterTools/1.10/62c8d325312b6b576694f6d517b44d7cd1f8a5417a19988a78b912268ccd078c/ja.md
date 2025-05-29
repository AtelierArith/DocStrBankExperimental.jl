```
flagfirst(iter)
```

最初の要素に対して `true`、それ以降は `false` となる `isfirst::Bool` を持つ `(isfirst, x)` を生成するイテレータで、`x` は `iter` からの要素です。

```jldoctest
julia> collect(flagfirst(1:3))
3-element Vector{Tuple{Bool, Int64}}:
 (1, 1)
 (0, 2)
 (0, 3)
```
