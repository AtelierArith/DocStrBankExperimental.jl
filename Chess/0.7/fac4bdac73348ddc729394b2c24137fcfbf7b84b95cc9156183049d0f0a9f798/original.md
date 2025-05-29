```
isatbeginning(g::SimpleGame)::Bool
isatbeginning(g::Game)::Bool
```

Return `true` if we are at the beginning of the game, and `false` otherwise.

We can be at the beginning of the game either because we haven't yet added any moves to the game, or because we have stepped back to the beginning.

# Examples

```julia-repl
julia> g = SimpleGame();

julia> isatbeginning(g)
true

julia> domove!(g, "e4");

julia> isatbeginning(g)
false

julia> back!(g);

julia> isatbeginning(g)
true
```
