```
plot_graphviz(g, attributes; path = zeros(Int, nv(mat)))
```

Render graph `g` in **iJulia** using `Graphviz` engines.

#### Arguments

  * `g::AbstractSimpleWeightedGraph`: a graph representation to export
  * `attributes::AttributeDict`: Render with own set of plotting attributes (see http://www.graphviz.org/ for details)
  * (optional) `path = []`: Int-Array of nodes. Nodes and their edges are drawn in red color (i.e. shortest path)
  * (optional) `colors = zeros(Int, nv(mat))`: Color nodes using Brewer Color Scheme (max 9 colors).
  * (optional) `scale = 3.0`: Scale your plot
  * (optional) `landscape = false`: if true > set `rankdir` to `LR`
