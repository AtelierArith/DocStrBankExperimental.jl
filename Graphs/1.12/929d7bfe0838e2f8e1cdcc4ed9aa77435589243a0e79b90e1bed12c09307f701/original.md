```
simplecycleslength(dg::DiGraph, ceiling = 10^6)
```

Search all cycles of the given directed graph, using Johnson's algorithm, and return a tuple representing the cycle length and the number of cycles.

### Implementation Notes

To get an idea of the possible number of cycles, using function `maxsimplecycles(dg::DiGraph, byscc::Bool = true)` on the directed graph.

If the `ceiling` is reached (`ncycles = ceiling`), the output is only a subset of the cycles lengths.

### References

  * [Johnson](http://epubs.siam.org/doi/abs/10.1137/0204007)

# Examples

```jldoctest
julia> using Graphs

julia> simplecycleslength(complete_digraph(16))
([0, 1, 1, 1, 1, 1, 2, 10, 73, 511, 3066, 15329, 61313, 183939, 367876, 367876], 1000000)

julia> simplecycleslength(wheel_digraph(16))
([0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1, 0], 1)
```
