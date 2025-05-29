```
element_coloring(fes, n2e, ellist::Vector{IT} = IT[]) where {IT<:Integer}
```

Find coloring of the elements such that no two elements of the same color share a node.

Returns the colors of the elements (color here means an integer), and a list of the unique colors (numbers).

`ellist` = list of elements to be assigned colors; other element colors may be looked at
