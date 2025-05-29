```
addmoves!(g::Game, moves::Vararg{Union{Move, String}})
```

Adds a sequence of moves to the game `g` at the current node.

The moves can be either `Move` values or strings. In the case of strings, the function tries to parse them first as UCI moves, then as SAN moves.

This function works by calling `addmove!` repeatedly for all input moves. It's the caller's responsibility to ensure that all moves are legal and unambiguous.
