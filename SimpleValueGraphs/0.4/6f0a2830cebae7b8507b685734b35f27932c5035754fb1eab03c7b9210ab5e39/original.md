```
get_edgeval(e::AbstractValEdge, :)
```

Return the values attached to the edge `e`.

# Examples

```jldoctest
julia> e = ValEdge(1, 2, ("xyz", 123));

julia> get_edgeval(e, :)
("xyz", 123)

julia> e = ValDiEdge(1, 2, (weight=2.5,));

julia> get_edgeval(e, :)
(weight = 2.5,)
```
