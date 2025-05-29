```
rand_edge_split(g::GNNGraph, frac; bidirected=is_bidirected(g)) -> g1, g2
```

Randomly partition the edges in `g` to form two graphs, `g1` and `g2`. Both will have the same number of nodes as `g`. `g1` will contain a fraction `frac` of the original edges,  while `g2` wil contain the rest.

If `bidirected = true` makes sure that an edge and its reverse go into the same split. This option is supported only for bidirected graphs with no self-loops and multi-edges.

`rand_edge_split` is tipically used to create train/test splits in link prediction tasks.
