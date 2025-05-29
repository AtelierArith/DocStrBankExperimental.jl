```
isparentof(node, edge)
ischildof(node, edge)
```

`true` if `node` is the tail / head, or parent / child, of `edge`; `false` otherwise. Assumes that the edge's direction is correct, meaning its field `ischild1` is reliable (in sync with the rooting).

See also: [`getparent`](@ref), [`getchild`](@ref), [`isrootof`](@ref)
