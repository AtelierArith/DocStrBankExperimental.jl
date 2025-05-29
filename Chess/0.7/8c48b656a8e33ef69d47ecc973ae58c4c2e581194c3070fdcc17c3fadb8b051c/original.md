```
@game
```

A macro for initializing a `Game` with a number of moves.

Castling moves must be indicated without a hyphen (i.e. "OO" or "OOO") in order to satisfy Julia's parser.

# Examples

```julia-repl
julia> @game d4 Nf6 c4 e6 Nc3 Bb4 Qc2 OO
Game:
 1. d4 Nf6 2. c4 e6 3. Nc3 Bb4 4. Qc2 O-O *
```
