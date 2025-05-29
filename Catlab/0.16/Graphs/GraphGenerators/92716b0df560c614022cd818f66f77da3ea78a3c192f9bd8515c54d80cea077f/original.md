```
expected_degree_graph(GraphType, ω)
```

Given a vector of expected degrees `ω` indexed by vertex, create a random undirected graph in which vertices `i` and `j` are connected with probability `ω[i]*ω[j]/sum(ω)`.

### Optional Arguments

  * `seed=-1`: set the RNG seed.
  * `rng`: set the RNG directly

### Implementation Notes

The algorithm should work well for `maximum(ω) << sum(ω)`. As `maximum(ω)` approaches `sum(ω)`, some deviations from the expected values are likely.

### References

  * Connected Components in Random Graphs with Given Expected Degree Sequences, Linyuan Lu and Fan Chung. [https://link.springer.com/article/10.1007%2FPL00012580](https://link.springer.com/article/10.1007%2FPL00012580)
  * Efficient Generation of Networks with Given Expected Degrees, Joel C. Miller and Aric Hagberg. [https://doi.org/10.1007/978-3-642-21286-4_10](https://doi.org/10.1007/978-3-642-21286-4_10)
  * https://github.com/JuliaGraphs/LightGraphs.jl/blob/2a644c2b15b444e7f32f73021ec276aa9fc8ba30/src/SimpleGraphs/generators/randgraphs.jl#L187
