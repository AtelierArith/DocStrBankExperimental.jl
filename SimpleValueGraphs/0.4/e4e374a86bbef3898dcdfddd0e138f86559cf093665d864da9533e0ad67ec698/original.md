```
add_edge!(g::AbstractValGraph, s, d, [values])
add_edge!(g::AbstractValGraph, s, d; val=value)
```

Add an edge `e = (s, d, values)` to a graph `g` and set the edge values.

If `g` does not have and edge values, `values` can be omitted.

For graphs with a single edge value, that value can also be specified with the `val` keyword argument.

Return `true` if the edge was added successfully, otherwise return `false`. If the edge already exists, return `false` but still change the edge values.
