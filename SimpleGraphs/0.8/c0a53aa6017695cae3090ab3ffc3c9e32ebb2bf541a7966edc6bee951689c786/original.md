`trim(G)` returns a copy of `G` with all isolated vertices removed.

`trim(G,d)` returns a copy of `G` in which we iteratively remove all vertices of degree `d` or smaller. For example, if `G` is a tree, `trim(G,1)` will eventually remove all vertices.
