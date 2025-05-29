`dist(G,u,v)` finds the length of a shortest path from `u` to `v` in `G`. Returns `-1` if no such path exists.

`dist(G,u)` finds the distance from `u` to all other vertices in `G`. Result is returned as a `Dict`.

`dist(G)` finds all pairs of distances in `G`. Result is a `Dict` whose `[u,v]` entry is the distance from `u` to `v`.
