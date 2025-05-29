```
chordal_graph(G::LabeledGraph, π̄::Array{Symbol, 1})
```

Return a chordal graph built from 'G' using the elimination order 'π̄'.

The returned graph is created from 'G' by iterating over the vertices of 'G', according to  the order 'π̄', and for each vertex, connecting all the neighbors that appear later in the  order.
