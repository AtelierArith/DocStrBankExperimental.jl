```
pinned(b::Board)
```

The set of squares containing pinned pieces for the current side to move.

# Examples

```julia-repl
julia> b = fromfen("2r4b/1kp5/8/2P1Q3/1P6/2K1P2r/8/8 w - -");

julia> pprint(b, highlight=pinned(b))
+---+---+---+---+---+---+---+---+
|   |   | r |   |   |   |   | b |
+---+---+---+---+---+---+---+---+
|   | k | p |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   |   |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   | P |   |*Q*|   |   |   |
+---+---+---+---+---+---+---+---+
|   | P |   |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   | K |   |*P*|   |   | r |
+---+---+---+---+---+---+---+---+
|   |   |   |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   |   |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
2r4b/1kp5/8/2P1Q3/1P6/2K1P2r/8/8 w - -
```
