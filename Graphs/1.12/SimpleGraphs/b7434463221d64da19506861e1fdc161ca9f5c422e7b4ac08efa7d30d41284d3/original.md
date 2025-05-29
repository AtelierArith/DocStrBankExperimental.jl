```
expected_degree_graph(ω)
```

Given a vector of expected degrees `ω` indexed by vertex, create a random undirected graph in which vertices `i` and `j` are connected with probability `ω[i]*ω[j]/sum(ω)`.

### Optional Arguments

  * `rng=nothing`: set the Random Number Generator.
  * `seed=nothing`: set the RNG seed.

### Implementation Notes

The algorithm should work well for `maximum(ω) << sum(ω)`. As `maximum(ω)` approaches `sum(ω)`, some deviations from the expected values are likely.

### References

  * Connected Components in Random Graphs with Given Expected Degree Sequences, Linyuan Lu and Fan Chung. [https://link.springer.com/article/10.1007%2FPL00012580](https://link.springer.com/article/10.1007%2FPL00012580)
  * Efficient Generation of Networks with Given Expected Degrees, Joel C. Miller and Aric Hagberg. [https://doi.org/10.1007/978-3-642-21286-4_10](https://doi.org/10.1007/978-3-642-21286-4_10)

# Examples

```
# 1)
julia> using Graphs

julia> g = expected_degree_graph([3, 1//2, 1//2, 1//2, 1//2])
{5, 3} undirected simple Int64 graph

julia> print(degree(g))
[3, 0, 1, 1, 1]

# 2)
julia> g = expected_degree_graph([0.5, 0.5, 0.5], seed=123)
{3, 1} undirected simple Int64 graph

julia> print(degree(g))
[1, 0, 1]
```
