```
function plot_tree(graph::AbstractGraph; verbose = 0, maxdepth = 6)

Visualize the computational graph as a tree using ete3 python package
```

#Arguments

  * `graph::AbstractGraph`        : the computational graph struct to visualize
  * `verbose=0`   : the amount of information to show
  * `maxdepth=6`  : deepest level of the computational graph to show
