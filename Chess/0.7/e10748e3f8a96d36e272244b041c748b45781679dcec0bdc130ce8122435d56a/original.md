```
decodemoves(bytes::Vector{UInt8}; annotations = false, fen = START_FEN)
```

Converts a byte array created by `encodemoves` back to a game.

If `annotations` is `false`, the return value is a `SimpleGame`, while if it is `true`, the return value is a `Game`.
