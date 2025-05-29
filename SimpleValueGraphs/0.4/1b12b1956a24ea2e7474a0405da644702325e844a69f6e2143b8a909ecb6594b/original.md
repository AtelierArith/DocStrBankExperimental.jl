```
add_vertex!(g::AbstractValGraph[, values])
add_vertex!(g::AbstractValGraph; val=value)
```

Add an vertex to a graph `g` and set the vertex values.

If `g` does not have vertex values, `values` can be omitted.

For graphs with a single vertex value, that value can also be specified with the `val` keyword argument.

Return `true` if the vertex was added successfully, otherwise return `false`.
