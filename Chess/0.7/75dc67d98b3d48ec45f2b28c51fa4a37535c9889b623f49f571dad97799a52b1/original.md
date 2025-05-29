```
rookattacks(b::Board, s::Square)
```

The set of squares a rook on square `s` would attack on this board.

Both empty squares and squares occupied by enemy or friendly pieces are included in the set.

# Examples

```julia-repl
julia> b = fromfen("2r2k2/8/8/8/2R3P1/8/4P3/3K4 w - -");

julia> pprint(b, highlight=rookattacks(b, SQ_C4))
+---+---+---+---+---+---+---+---+
|   |   |*r*|   |   | k |   |   |
+---+---+---+---+---+---+---+---+
|   |   | * |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   | * |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   | * |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
| * | * | R | * | * | * |*P*|   |
+---+---+---+---+---+---+---+---+
|   |   | * |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   | * |   | P |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   | * | K |   |   |   |   |
+---+---+---+---+---+---+---+---+
2r2k2/8/8/8/2R3P1/8/4P3/3K4 w - -
```
