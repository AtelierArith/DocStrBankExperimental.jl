```
dominating_set(g, MinimalDominatingSet(); seed=-1)
```

Find a set of vertices that consitute a dominating set (all vertices in `g` are either adjacent to a vertex  in the set or is a vertex in the set) and it is not possible to delete a vertex from the set  without sacrificing the dominating property.

### Implementation Notes

Initially, every vertex is in the dominating set. In some random order, we check if the removal of a vertex from the set will destroy the  dominating property. If no, the vertex is removed from the dominating set.

### Performance

Runtime: $\mathcal{O}(|V|+|E|)$ Memory: $\mathcal{O}(|V|)$

### Optional Arguments

  * If `seed >= 0`, a random generator is seeded with this value.
