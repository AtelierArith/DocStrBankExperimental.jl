```
static_fitness_model(m, fitness)
```

Generate a random graph with $|fitness|$ vertices and `m` edges, in which the probability of the existence of $Edge_{ij}$ is proportional to $fitness_i × fitness_j$.

### Optional Arguments

  * `rng=nothing`: set the Random Number Generator.
  * `seed=nothing`: set the RNG seed.

### Performance

Time complexity is $\mathcal{O}(|V| + |E| log |E|)$.

### References

  * Goh K-I, Kahng B, Kim D: Universal behaviour of load distribution in scale-free networks. Phys Rev Lett 87(27):278701, 2001.

## Examples

```
julia> g = static_fitness_model(5, [1, 1, 0.5, 0.1])
{4, 5} undirected simple Int64 graph

julia> edges(g) |> collect
5-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 2 => 3
 Edge 2 => 4
```

```
julia> using Graphs

julia> g = static_fitness_model(5, [1, 1, 0.5, 0.1], seed=123)
{4, 5} undirected simple Int64 graph

julia> edges(g) |> collect
5-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 2 => 3
 Edge 2 => 4
 Edge 3 => 4
```
