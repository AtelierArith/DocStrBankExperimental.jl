```
skeleton(n::Integer, I) -> g, S
skeleton(g, I) -> g, S
```

Perform the undirected PC skeleton algorithm for a set of `1:n` variables using the test `I`. Start with a subgraph `g` or the complete undirected graph on `n` vertices. Returns skeleton graph and separating set.
