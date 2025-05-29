```
@addmoves!(game, moves...)
```

A macro for adding a sequence of moves to the game `game`.

Castling moves must be indicated without a hyphen (i.e. "OO" or "OOO") in order to satisfy Julia's parser.

# Examples

```julia-repl
julia> g = @game e4 c5
Game:
 1. e4 c5 *

julia> @addmoves! g Nf3 Nc6
Game:
 1. e4 c5 2. Nf3 Nc6 *

julia> g = @game e4 e5 Nf3; back!(g); back!(g)
Game:
 1. e4 * e5 2. Nf3

julia> @addmoves! g c5 b4 cxb4
Game:
 1. e4 e5 (1... c5 2. b4 cxb4 *) 2. Nf3
```
