```
bishopattacks(b::Board, s::Square)
```

The set of squares a bishop on square `s` would attack on this board.

Both empty squares and squares occupied by enemy or friendly pieces are included in the set.

# Examples

```julia-repl
julia> b = fromfen("5k2/8/4q3/8/2B5/8/4P3/3K4 w - -");

julia> pprint(b, highlight=bishopattacks(b, SQ_C4))
+---+---+---+---+---+---+---+---+
|   |   |   |   |   | k |   |   |
+---+---+---+---+---+---+---+---+
|   |   |   |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
| * |   |   |   |*q*|   |   |   |
+---+---+---+---+---+---+---+---+
|   | * |   | * |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   | B |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   | * |   | * |   |   |   |   |
+---+---+---+---+---+---+---+---+
| * |   |   |   |*P*|   |   |   |
+---+---+---+---+---+---+---+---+
|   |   |   | K |   |   |   |   |
+---+---+---+---+---+---+---+---+
5k2/8/4q3/8/2B5/8/4P3/3K4 w - -
```
