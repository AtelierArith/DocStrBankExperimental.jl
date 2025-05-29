```
simplecyclescount(dg::DiGraph, ceiling = 10^6)
```

Count the number of cycles in a directed graph, using Johnson's algorithm. Return the minimum of the ceiling and the number of cycles.

### Implementation Notes

The `ceiling` is here to avoid memory overload if there are a lot of cycles in the graph. Default value is 10^6, but it can be higher or lower. You can use the function `maxsimplecycles(dg::DiGraph, byscc::Bool = true)` to get an idea of the theoretical maximum number or cycles.

### References

  * [Johnson](http://epubs.siam.org/doi/abs/10.1137/0204007)

# Examples

```jldoctest
julia> using Graphs

julia> simplecyclescount(complete_digraph(6))
409
```
