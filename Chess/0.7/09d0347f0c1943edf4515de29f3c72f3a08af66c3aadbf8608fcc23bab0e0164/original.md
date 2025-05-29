```
flop(b::Board)
```

Returns an identical board, but flipped horizontally.

All castling rights will be deleted.

# Examples

```julia-repl
julia> b = @startboard d4 Nf6 c4 e6 Nc3 Bb4 e3 OO
Board (rnbq1rk1/pppp1ppp/4pn2/8/1bPP4/2N1P3/PP3PPP/R1BQKBNR w KQ -):
 r  n  b  q  -  r  k  -
 p  p  p  p  -  p  p  p
 -  -  -  -  p  n  -  -
 -  -  -  -  -  -  -  -
 -  b  P  P  -  -  -  -
 -  -  N  -  P  -  -  -
 P  P  -  -  -  P  P  P
 R  -  B  Q  K  B  N  R

julia> flop(b)
Board (1kr1qbnr/ppp1pppp/2np4/8/4PPb1/3P1N2/PPP3PP/RNBKQB1R w - -):
 -  k  r  -  q  b  n  r
 p  p  p  -  p  p  p  p
 -  -  n  p  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  P  P  b  -
 -  -  -  P  -  N  -  -
 P  P  P  -  -  -  P  P
 R  N  B  K  Q  B  -  R
```
