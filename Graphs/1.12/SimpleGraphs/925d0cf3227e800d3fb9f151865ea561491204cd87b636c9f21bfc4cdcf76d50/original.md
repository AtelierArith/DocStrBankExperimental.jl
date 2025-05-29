```
dorogovtsev_mendes(n)
```

Generate a random `n` vertex graph by the Dorogovtsev-Mendes method (with `n \ge 3`).

The Dorogovtsev-Mendes process begins with a triangle graph and inserts `n-3` additional vertices. Each time a vertex is added, a random edge is selected and the new vertex is connected to the two endpoints of the chosen edge. This creates graphs with many triangles and a high local clustering coefficient.

It is often useful to track the evolution of the graph as vertices are added, you can access the graph from the `t`th stage of this algorithm by accessing the first `t` vertices with `g[1:t]`.

### References

  * http://graphstream-project.org/doc/Generators/Dorogovtsev-Mendes-generator/
  * https://arxiv.org/pdf/cond-mat/0106144.pdf#page=24

# Examples

```jldoctest
julia> using Graphs

julia> dorogovtsev_mendes(10)
{10, 17} undirected simple Int64 graph

julia> dorogovtsev_mendes(11, seed=123)
{11, 19} undirected simple Int64 graph
```
