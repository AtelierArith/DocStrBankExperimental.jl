`euler_char(G::UndirectedGraph)` computes the Euler characteristic  of the graph `G` with its associated rotation system.  Specifically, `euler_char(G)` returns `NV(G) - NE(G) + NF(G)`.

*Requires that the graph is connected and has at least one edge.*
