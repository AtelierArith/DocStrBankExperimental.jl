```
orient_unshielded(g, dg, S)
```

Orient unshielded triples using the separating sets. `g` is an undirected graph containing edges of unknown direction, `dg` is an directed graph containing edges of known direction and  both `v=>w` and `w=>v`if the direction of `Edge(v,w)``is unknown.`S` are the separating sets of edges.

Returns `g, dg`.
