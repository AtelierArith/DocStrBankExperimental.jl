```
encodemoves(g::SimpleGame)::Vector{UInt8}
encodemoves(g::Game)::Vector{UInt8}
```

Encodes the moves of the game as a byte vector.

This is useful for storing games in a binary format significantly more compact than PGN.

The inverse function `decodemoves` is used to convert back to a game.
