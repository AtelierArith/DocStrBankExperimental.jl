```
sum(g)
```

`g`のエッジの数を返します。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph([0 1 0; 1 0 1; 0 1 0]);

julia> sum(g)
2
```
