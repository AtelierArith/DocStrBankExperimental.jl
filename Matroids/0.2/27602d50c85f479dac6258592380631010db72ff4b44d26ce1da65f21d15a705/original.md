This is a bare-bones implementation of multigraphs. These graphs are  undirected and may have loops. All edges may appear multiple times in  the multigraph.

There are two constructors:

  * `EasyMultiGraph(n::Int)` – create a multigraph with `n` vertices (and no edges)
  * `EasyMultiGraph(g::graph)` – create a multigraph from a graph `g` with all edge multipliticies equal to 1.

Note that edges may be added or removed, but the number of vertices cannot be changed. 

See: `add!` and `rem!`
