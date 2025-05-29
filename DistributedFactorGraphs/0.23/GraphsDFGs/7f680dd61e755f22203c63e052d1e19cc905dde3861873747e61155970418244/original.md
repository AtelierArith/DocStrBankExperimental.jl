```julia
findShortestPathDijkstra(
    dfg,
    from,
    to;
    regexVariables,
    regexFactors,
    tagsVariables,
    tagsFactors,
    typeVariables,
    typeFactors,
    solvable,
    initialized
)

```

Speciallized function available to only GraphsDFG at this time.

Notes

  * Has option for various types of filters (increases memory usage)

Example

```julia
using IncrementalInference

# canonical example graph as example
fg = generateGraph_Kaess()

@show path = findShortestPathDijkstra(fg, :x1, :x3)
@show isVariable.(fg, path)
@show isFactor.(fg, path)
```

DevNotes

  * TODO expand to other AbstractDFG entities.
  * TODO use of filter resource consumption can be improved.

Related

[`findFactorsBetweenNaive`](@ref), `Graphs.dijkstra_shortest_paths`
