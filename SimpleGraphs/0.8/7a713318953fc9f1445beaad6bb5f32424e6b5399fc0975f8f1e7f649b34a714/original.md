`euler(G,u,v)` finds an Euler trail in `G` starting at `u` and ending at `v` returned as a list of vertices (in the order they are visited on the trail).

`euler(G,u)` finds an Euler tour beginning and ending at `u`. Alternatively, call `euler(G)` and the initial/final vertex will be selected for you.

Note: The algorithm will succeed even if there are isolated vertices in the graph (just don't choose an isolated vertex as the first/last).

If no Euler trail/tour exists, an empty list is returned.
