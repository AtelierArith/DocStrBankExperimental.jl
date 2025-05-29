```
 (graph,crefs)=graph_ps_degopt(a; input=:A)
```

Generates the same polynomial as [`graph_ps`](@ref), i.e., the graph for the Paterson–Stockmeyer procedure with monomial basis coefficieents. However, it does so by wrapping a call to [`graph_degopt`](@ref), resulting in more degrees of freedom in `crefs`.
