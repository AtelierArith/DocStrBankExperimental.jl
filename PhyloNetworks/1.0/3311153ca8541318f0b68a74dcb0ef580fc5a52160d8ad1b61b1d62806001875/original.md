```
getpartneredge(edge::Edge)
getpartneredge(edge::Edge, node::Node)
```

Edge that is the hybrid partner of `edge`, meaning that is has the same child `node` as `edge`. This child `node` is given as an argument in the second method. Assumptions, not checked:

  * no in-coming polytomy: a node has 0, 1 or 2 parents, no more
  * when `node` is given, it is assumed to be the child of `edge` (the first method calls the second).

See also: [`getparent`](@ref), [`getchild`](@ref)
