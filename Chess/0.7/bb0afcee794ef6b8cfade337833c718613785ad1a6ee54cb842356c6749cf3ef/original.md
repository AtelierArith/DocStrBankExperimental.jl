```
addmove!(g::Game, m::Move)
addmove!(g::Game, m::String)
```

Adds the move `m` to the game `g` at the current node.

If the supplied move is a string, this function tries to parse the move as a UCI move first, then as a SAN move.

The move `m` must be a legal move from the current node board position. A new game node with the board position after the move has been made is added to the end of the current node's children vector, and that node becomes the current node of the game.

The move `m` is assumed to be a legal move. It's the caller's responsibility to ensure that this is the case.
