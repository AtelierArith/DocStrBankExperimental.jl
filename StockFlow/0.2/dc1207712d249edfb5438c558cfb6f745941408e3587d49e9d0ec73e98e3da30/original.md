Return true if a given list of edges is a walk; that the target for each edge is the source of the next.  Empty list of edges counts as a walk.

Note, negative edges come after positive edges:

```julia-repl
julia> using StockFlow; using StockFlow.Syntax;
julia> cl = (@cl A => +B, B => -C, C => +D, D => -E);
julia> is_walk(cl, [1,3,2,4])
true
```
