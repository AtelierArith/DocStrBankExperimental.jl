```
pprint(b::Board, color = false, highlight = SS_EMPTY, unicode = false)
```

Pretty-print a `Board` to the standard output.

On terminals with 24-bit color support, use `color = true` for a colored board. Use the parameter `highlight` to include a `SquareSet` you want to be highlighted.

Use `unicode = true` for Unicode piece output, if your font and terminal supports it.

# Examples

```julia-repl
julia> pprint(startboard(), highlight = SquareSet(SQ_D4, SQ_E4, SQ_D5, SQ_E5))
+---+---+---+---+---+---+---+---+
| r | n | b | q | k | b | n | r |
+---+---+---+---+---+---+---+---+
| p | p | p | p | p | p | p | p |
+---+---+---+---+---+---+---+---+
|   |   |   |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   |   | * | * |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   |   | * | * |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   |   |   |   |   |   |   |
+---+---+---+---+---+---+---+---+
| P | P | P | P | P | P | P | P |
+---+---+---+---+---+---+---+---+
| R | N | B | Q | K | B | N | R |
+---+---+---+---+---+---+---+---+
rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq -
```
