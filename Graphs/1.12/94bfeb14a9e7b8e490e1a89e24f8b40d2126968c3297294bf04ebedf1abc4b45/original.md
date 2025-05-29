```
independent_set(g, DegreeIndependentSet())
```

Obtain an [independent set](https://en.wikipedia.org/wiki/Independent_set_(graph_theory)) of `g` using a greedy heuristic based on the degree of the vertices.

### Implementation Notes

A vertex is said to be valid if it is not in the independent set or adjacent to any vertex in the independent set. Initilalise the independent set to an empty set and iteratively choose the vertex that is  adjacent to the fewest valid vertices in the independent set until all vertices are invalid.

### Performance

Runtime: O((|V|+|E|)*log(|V|)) Memory: O(|V|)
