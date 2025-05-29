```
erdos_renyi(n::Int, p::Real, G=Graph; seed=-1)
erdos_renyi(n::Int, m::Int, G=Graph; seed=-1)
```

Creates an [Erdős–Rényi](http://en.wikipedia.org/wiki/Erdős–Rényi_model) random graph of type `G` with `n` vertices. Edges are added between pairs of vertices with probability `p` in the first method. In the second method `m` edges are randomly chosen insted.

Undirected graphs are created by default. Directed graphs can be created passing a directed graph type as last argument (e.g. `DiGraph`)

Note also that Erdős–Rényi graphs may be generated quickly using `erdos_renyi(n, ne)` or the  `Graph(nv, ne)` constructor, which randomly select `ne` edges among all the potential edges.
