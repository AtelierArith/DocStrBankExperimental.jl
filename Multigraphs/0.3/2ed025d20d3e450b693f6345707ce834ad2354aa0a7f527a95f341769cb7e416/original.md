```
mul(e)
```

Return the multiplicity of the multiple edge `e`.

## Examples

```jltestdoc julia> using Graphs, Multigraphs

julia> me = MultipleEdge(1, 2, 3) Multiple edge 1 => 2 with multiplicity 3

julia> mul(me) 3
