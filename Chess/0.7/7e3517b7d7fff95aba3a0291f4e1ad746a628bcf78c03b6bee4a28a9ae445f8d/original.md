```
attacksto(b::Board, s::Square)
```

The set of squares containing pieces of either color which attack square `s`.

# Examples

```julia-repl
julia> b = fromfen("r1bqkbnr/pppp1ppp/2n5/4p3/3PP3/5N2/PPP2PPP/RNBQKB1R b KQkq - 0 3");

julia> pprint(b, highlight=attacksto(b, SQ_D4))
+---+---+---+---+---+---+---+---+
| r |   | b | q | k | b | n | r |
+---+---+---+---+---+---+---+---+
| p | p | p | p |   | p | p | p |
+---+---+---+---+---+---+---+---+
|   |   |*n*|   |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   |   |   |*p*|   |   |   |
+---+---+---+---+---+---+---+---+
|   |   |   | P | P |   |   |   |
+---+---+---+---+---+---+---+---+
|   |   |   |   |   |*N*|   |   |
+---+---+---+---+---+---+---+---+
| P | P | P |   |   | P | P | P |
+---+---+---+---+---+---+---+---+
| R | N | B |*Q*| K | B |   | R |
+---+---+---+---+---+---+---+---+
r1bqkbnr/pppp1ppp/2n5/4p3/3PP3/5N2/PPP2PPP/RNBQKB1R b KQkq -
```
