```
isatend(g::SimpleGame)::Bool
isatend(g::Game)::Bool
```

Return `true` if we are at the end of the game, and `false` otherwise.

# Examples

```julia-repl
julia> g = SimpleGame();

julia> isatend(g)
true

julia> domove!(g, "Nf3");

julia> isatend(g)
true

julia> back!(g);

julia> isatend(g)
false
```
