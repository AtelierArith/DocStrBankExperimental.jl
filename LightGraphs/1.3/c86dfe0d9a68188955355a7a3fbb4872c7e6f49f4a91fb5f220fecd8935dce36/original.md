```
dominating_set(g, DegreeDominatingSet())
```

Obtain a [dominating set](https://en.wikipedia.org/wiki/Dominating_set) using a greedy heuristic.

### Implementation Notes

A vertex is said to be dominated if it is in the dominating set or adjacent to a vertex  in the dominating set. Initialise the dominating set to an empty set and iteratively choose the vertex that would  dominate the most undominated vertices.

### Performance

Runtime: $\mathcal{O}((|V|+|E|)*log(|V|))$ Memory: $\mathcal{O}(|V|)$ Approximation Factor: `ln(maximum(degree(g)))+2`
