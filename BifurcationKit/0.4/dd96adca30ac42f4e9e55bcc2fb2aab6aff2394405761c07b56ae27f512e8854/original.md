```julia
get_branch(diagram, code)

```

Return the part of the diagram (bifurcation diagram) by recursively descending down the diagram using the `Int` valued tuple `code`. For example `get_branch(diagram, (1,2,3,))` returns `diagram.child[1].child[2].child[3]`.
