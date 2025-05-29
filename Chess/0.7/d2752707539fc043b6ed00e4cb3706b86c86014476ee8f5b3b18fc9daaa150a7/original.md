```
continuations(n::GameNode)::Vector{Move}
continuations(g::Game)::Vector{Move}
```

All moves at this node in the game tree.

One move for each child node of the current node. The first element is the main line.

# Examples

```julia-repl
julia> g = Game();

julia> addmoves!(g, "e4", "e5");

julia> back!(g);

julia> addmove!(g, "c5");

julia> back!(g);

julia> continuations(g)
2-element Array{Move,1}:
 Move(e7e5)
 Move(c7c5)
```
