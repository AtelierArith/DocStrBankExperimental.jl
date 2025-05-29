```
@domoves!(game, moves...)
```

A macro for adding moves to `game`, deleting existing continuations.

Castling moves must be indicated without a hyphen (i.e. "OO" or "OOO") in order to satisfy Julia's parser.

This macro will delete any pre-existing continuations from the current point in the game. If this is not desired, use the `@addmoves!` macro instead.

# Examples

```julia-repl
julia> g = @game e4 e5 Nf3; back!(g); back!(g)
Game:
 1. e4 * e5 2. Nf3

julia> @domoves! g c5 b4 cxb4
Game:
 1. e4 c5 2. b4 cxb4 *
```
