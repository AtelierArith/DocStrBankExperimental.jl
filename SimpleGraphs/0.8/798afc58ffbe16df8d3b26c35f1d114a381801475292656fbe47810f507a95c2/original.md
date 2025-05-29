`lex(G,H)` computes the lexicographic product of the graphs `G` and `H`. The vertex set of this graph is the set of all ordered pairs `(g,h)` (with `g` a vertex of `G` and `h` a vertex of `H` in which we have the edge `(g,h)~(g',h')` if either `g~g'` in `G` or else `g=g` and `h~h'`.

We can use the notation `G[H]` also to create `lex(G,H)`.
