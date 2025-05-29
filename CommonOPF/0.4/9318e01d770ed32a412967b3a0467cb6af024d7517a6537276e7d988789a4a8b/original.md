```
function Network(d::Dict; directed::Union{Bool,Missing}=missing)
```

Construct a `Network` from a dictionary that has at least keys for:

1. `:Conductor`, a vector of dicts with [Conductor](@ref) specs
2. `:Network`, a dict with at least `:substation_bus`

If `directed` is missing then the graph is directed only if the number of busses and edges imply a      radial graph.
