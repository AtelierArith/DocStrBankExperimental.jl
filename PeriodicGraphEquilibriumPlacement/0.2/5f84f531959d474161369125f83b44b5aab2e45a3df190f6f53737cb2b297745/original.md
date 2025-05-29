```
equilibrium(g::PeriodicGraph)
```

Return an equilibrium placement for the vertices of the graph, defined as a list of positions such that each vertex is at the barycentre of its neighbors.

The returned equilibrium placement is such that the first vertex of the graph is at the origin of the space.
