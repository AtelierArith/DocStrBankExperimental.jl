```
domoves!(g::SimpleGame, moves::Vararg{Union{Move, String}})
domoves!(g::Game, moves::Vararg{Union{Move, String}})
```

Adds a sequence of new moves at the current location in the game move list.

The moves can be either `Move` values or strings. In the case of strings, the function tries to parse them first as UCI moves, then as SAN moves.

If we are at the end of the game, all previous moves are kept, and the new moves are added at the end. If we are at any earlier point in the game (because we have taken back one or more moves), the existing game continuation will be deleted and replaced by the new moves. All variations starting at this point in the game will also be deleted. If you want to add the new moves as a variation instead, make sure you use the `Game` type instead of `SimpleGame`, and use `addmoves!` instead of `domoves!`.
