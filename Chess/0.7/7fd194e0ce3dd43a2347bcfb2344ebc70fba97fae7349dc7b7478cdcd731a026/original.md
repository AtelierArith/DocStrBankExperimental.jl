```
variationtosan(board::Board, v::Vector{Move};
               startply=1, movenumbers=true)::String
```

Converts a variation to a string in short algebraic notation.

The vector of moves `v` should be a sequence of legal moves from the board position. If `movenumbers` is `true`, move numbers will be included in the string. The moves are numbered from 1, unless some other variable is supplied through the `startply` parameter.

# Examples

```julia-repl
julia> b = startboard();

julia> variationtosan(b, map(movefromstring, ["e2e4", "e7e5", "g1f3", "b8c6"]))
"1. e4 e5 2. Nf3 Nc6"
```
