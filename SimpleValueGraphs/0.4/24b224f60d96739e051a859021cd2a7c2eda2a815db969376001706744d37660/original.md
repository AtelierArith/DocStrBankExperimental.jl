```
get_edgeval(e::AbstractValEdge, key)
```

Return the value attached to the edge `e` for the key `key`.

# Examples

```jldoctest
julia> e = ValEdge(1, 2, (a=11.0, ));

julia> get_edgeval(e, 1) # use integer key
11.0

julia> get_edgeval(e, :a) # use symbolic key
11.0

```
