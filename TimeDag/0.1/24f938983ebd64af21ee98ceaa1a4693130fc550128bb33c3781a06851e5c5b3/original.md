```
coalign(x, [...; alignment::Alignment]) -> Node...
```

Given at least one node(s) `x`, or values that are convertible to nodes, align all of them.

We guarantee that all nodes that are returned will have the same alignment. The values of each node will correspond to the values of the input nodes.

The choice of alignment is controlled by `alignment`, which defaults to [`UNION`](@ref).
