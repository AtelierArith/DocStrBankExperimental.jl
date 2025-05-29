```
simplecycles(dg::::IsDirected)
```

Compute and return all cycles of the given directed graph using Johnson's algorithm.

### Performance

The number of cycles grows more than exponentially with the number of vertices, you might want to use the algorithm with a ceiling – [`simplecycles_iter`](@ref) – on large directed graphs (slightly slower). If you want to have an idea of the possible number of cycles, look at function `maxsimplecycles(dg::DiGraph, byscc::Bool = true)`. If you only need short cycles of a limited length, [`simplecycles_limited_length`](@ref) can be more efficient.

### References

  * [Johnson](http://epubs.siam.org/doi/abs/10.1137/0204007)

# Examples

```jldoctest
julia> simplecycles(complete_digraph(3))
5-element Array{Array{Int64,1},1}:
 [1, 2]
 [1, 2, 3]
 [1, 3]
 [1, 3, 2]
 [2, 3]
```
