```
get_edgeval(e::AbstractValEdge, :)
```

エッジ `e` に付随する値を返します。

# 例

```jldoctest
julia> e = ValEdge(1, 2, ("xyz", 123));

julia> get_edgeval(e, :)
("xyz", 123)

julia> e = ValDiEdge(1, 2, (weight=2.5,));

julia> get_edgeval(e, :)
(weight = 2.5,)
```
