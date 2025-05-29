```
PerfectEliminationOrder(elimination_algorithm=CliqueTrees.MCS())
```

Instance of [`AbstractOrder`](@ref) which computes a perfect elimination ordering when the underlying graph is [chordal](https://en.wikipedia.org/wiki/Chordal_graph). For non-chordal graphs, it computes a suboptimal ordering.

The `elimination_algorithm` must be an instance of `CliqueTrees.EliminationAlgorithm`.

!!! warning
    This order can only be applied for symmetric or bidirectional coloring problems. Furthermore, its theoretical guarantees only hold for decompression by substitution.


!!! danger
    This order is implemented as a package extension and requires loading [CliqueTrees.jl](https://github.com/AlgebraicJulia/CliqueTrees.jl).


# References

  * [Simple Linear-Time Algorithms to Test Chordality of Graphs, Test Acyclicity of Hypergraphs, and Selectively Reduce Acyclic Hypergraphs](https://epubs.siam.org/doi/10.1137/0213035), Tarjan and Yannakakis (1984)
