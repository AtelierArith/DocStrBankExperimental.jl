```
modularproduct(g::SimpleGraph{T}, h::SimpleGraph{T};
    vmatch=(g1,h1)->true,
    edgefilter=(g1,g2,h1,h2)->has_edge(g,g1,g2)==has_edge(g,h1,h2)) where T
```

Return the modular product `m` of graphs `g` and `h`, and a mapping whether the edge is connected or not. mapping g,h nodes to m nods is f(i, j) = (i - 1) * nv(h) + j and the reverse mapping is f(i) = (div(i - 1, nv(h)) + 1, mod(i - 1, nv(h))) + 1, where i in g and j in h.
