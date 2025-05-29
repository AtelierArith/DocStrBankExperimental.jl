```
inputvertex(name, size)
```

Return an immutable input type vertex with the given `name` and `size`.

Typically used as "entry" point to a computation graph.

# Examples

```jldoctest
julia> using NaiveNASlib

julia> inputvertex("input", 5)
InputSizeVertex(InputVertex(input, outputs=[]), 5)

```
