```
variationtosan(g::SimpleGame, v::Vector{Move}; movenumbers=true)::String
variationtosan(g::Game, v::Vector{Move}; movenumbers=true)::String
```

Converts a variation to a string in short algebraic notation.

The vector of moves `v` should be a sequence of legal moves from the current board position of the game. If `movenumbers` is `true`, move numbers will be included in the string.

# Examples

```julia-repl
julia> g = Game();

julia> domoves!(g, "d4", "Nf6", "c4", "e6", "Nf3");

julia> variationtosan(g, map(movefromstring, ["f8b4", "c1d2", "d8e7"]))
"3... Bb4+ 4. Bd2 Qe7"
```
