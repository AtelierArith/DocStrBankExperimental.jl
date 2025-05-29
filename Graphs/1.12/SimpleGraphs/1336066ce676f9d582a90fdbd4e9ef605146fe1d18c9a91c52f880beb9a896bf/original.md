```
barbell_graph(n1, n2)
```

Create a [barbell graph](https://en.wikipedia.org/wiki/Barbell_graph) consisting of a clique of size `n1` connected by an edge to a clique of size `n2`.

### Implementation Notes

Preserves the eltype of `n1` and `n2`. Will error if the required number of vertices exceeds the eltype. `n1` and `n2` must be at least 1 so that both cliques are non-empty. The cliques are organized with nodes `1:n1` being the left clique and `n1+1:n1+n2` being the right clique. The cliques are connected by and edge `(n1, n1+1)`.

# Examples

```jldoctest
julia> using Graphs

julia> barbell_graph(3, 4)
{7, 10} undirected simple Int64 graph

julia> barbell_graph(Int8(5), Int8(5))
{10, 21} undirected simple Int8 graph
```
