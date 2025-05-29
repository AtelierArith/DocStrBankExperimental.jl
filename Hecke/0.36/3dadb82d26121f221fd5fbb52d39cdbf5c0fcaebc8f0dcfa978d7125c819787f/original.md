```
hom(G::FinGenAbGroup, H::FinGenAbGroup; task::Symbol = :map) -> FinGenAbGroup, Map
```

Computes the group of all homomorpisms from $G$ to $H$ as an abstract group. If `task` is ":map", then a map $\phi$ is computed that can be used to obtain actual homomorphisms. This map also allows preimages. Set `task` to ":none" to not compute the map.
