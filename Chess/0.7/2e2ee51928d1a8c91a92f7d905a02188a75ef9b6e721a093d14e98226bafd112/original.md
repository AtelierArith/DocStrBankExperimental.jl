```
domove!(g::SimpleGame, m::Move)
domove!(g::SimpleGame, m::String)
domove!(g::Game, m::Move)
domove!(g::Game, m::String)
```

Adds a new move at the current location in the game move list.

If the supplied move is a string, this function tries to parse the move as a UCI move first, then as a SAN move.

If we are at the end of the game, all previous moves are kept, and the new move is added at the end. If we are at any earlier point in the game (because we have taken back one or more moves), the existing game continuation will be deleted and replaced by the new move. All variations starting at this point in the game will also be deleted. If you want to add the new move as a variation instead, make sure you use the `Game` type instead of `SimpleGame`, and use `addmove!` instead of `domove!`.

The move `m` is assumed to be a legal move. It's the caller's responsibility to ensure that this is the case.
