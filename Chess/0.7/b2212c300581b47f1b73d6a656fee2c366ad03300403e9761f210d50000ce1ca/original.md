```
ply(g::SimpleGame)
ply(g::Game)
```

The ply count of the current node.

Returns 1 for the root node, 2 for children of the root node, etc.

# Examples

```julia-repl
julia> g = Game();

julia> addmoves!(g, "d4", "Nf6", "c4", "g6", "Nc3", "Bg7");

julia> ply(g)
7

julia> back!(g);

julia> ply(g)
6

julia> tobeginning!(g);

julia> ply(g)
1
```
