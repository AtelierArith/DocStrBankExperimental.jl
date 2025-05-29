```
static_fitness_model(m, fitness_out, fitness_in)
```

Generate a random directed graph with $|fitness\_out + fitness\_in|$ vertices and `m` edges, in which the probability of the existence of $Edge_{ij}$ is proportional with respect to $i ∝ fitness\_out$ and $j ∝ fitness\_in$.

### Optional Arguments

  * `rng=nothing`: set the Random Number Generator.
  * `seed=nothing`: set the RNG seed.

### Performance

Time complexity is $\mathcal{O}(|V| + |E| log |E|)$.

### References

  * Goh K-I, Kahng B, Kim D: Universal behaviour of load distribution in scale-free networks. Phys Rev Lett 87(27):278701, 2001.

## Examples

```
julia> using Graphs

julia> g = static_fitness_model(6, [1, 0.2, 0.2, 0.2], [0.1, 0.1, 0.1, 0.9]; seed=123)
{4, 6} directed simple Int64 graph

julia> edges(g) |> collect
6-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 2 => 3
 Edge 2 => 4
 Edge 3 => 4
```
