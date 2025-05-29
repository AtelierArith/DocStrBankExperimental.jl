```
simplecycles_iter(dg::DiGraph, ceiling = 10^6)
```

Search all cycles of the given directed graph, using Johnson's algorithm, up to the ceiling (to avoid memory overload).

### Implementation Notes

If the graph is small, the ceiling will not be reached and `simplecycles(dg::DiGraph)` is more efficient. It avoids the overhead of the counting and testing if the ceiling is reached. It returns all the cycles of the directed graph if the `ceiling` is not reached, a subset of them otherwise.

To get an idea of the possible number of cycles, use function `maxsimplecycles(dg::DiGraph, byscc::Bool = true) on the directed graph.

### References

  * [Johnson](http://epubs.siam.org/doi/abs/10.1137/0204007)
