Return source vertex index of an edge of CausalLoopPM by index. Negative edges come after positive edges.

`julia-repl julia> using StockFlow; StockFlow.Syntax; julia> cl = (@cl A => +B, B => -C, C => +D); julia> sedge(cl, 3) 2`` The nodes are ordered A, B, C. The edges are ordered A => +B, C => +D, B => -C; so, the source index of the third edge is B, which has index 2.
