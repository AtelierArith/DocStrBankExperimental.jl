```
random_orientation_dag(g)
```

Generate a random oriented acyclical digraph. The function takes in a simple graph and a random number generator as an argument. The probability of each directional acyclic graph randomly being generated depends on the architecture of the original directed graph.

DAG's have a finite topological order; this order is randomly generated via "order = randperm()".

# Examples

```jldoctest
julia> using Graphs

julia> random_orientation_dag(complete_graph(10))
{10, 45} directed simple Int64 graph

julia> random_orientation_dag(star_graph(Int8(10)), seed=123)
{10, 9} directed simple Int8 graph
```
