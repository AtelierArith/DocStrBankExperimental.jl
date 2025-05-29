`greedy_color(G,seq)` creates a greedy proper coloring of the graph. The argument `seq` should be a 1-dimensional array containing every vertex exactly once (the function does not check this for you). The function follows that order in creating the coloring which is returned to you as a `Dict` mapping vertices to positive integers (representing the colors).

If `seq` is omitted, a random permutation of the vertices is used.
