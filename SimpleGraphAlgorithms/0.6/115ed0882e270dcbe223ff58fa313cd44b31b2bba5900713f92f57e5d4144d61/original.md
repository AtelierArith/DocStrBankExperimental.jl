`chromatic_poly(G)` computes the chromatic polynomial of the graph `G`. If `G` is a directe graph, this returns the chromatic polynomial of `G`'s underlying simple graph.

This function builds a datastructure to prevent computing the chromatic polynomial of the same graph twice. To do this, it uses frequent isomorphism checks.

See `size_cpm` and `reset_cpm`.
