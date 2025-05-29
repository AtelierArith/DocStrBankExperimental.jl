```
rotate(b::Board)
```

Returns an identical board, but rotated 180 degrees.

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

julia> rotate(b)
Board (rnbkqb1r/ppp3pp/3p1n2/4ppB1/8/2NP4/PPP1PPPP/1KR1QBNR b - -):
 r  n  b  k  q  b  -  r
 p  p  p  -  -  -  p  p
 -  -  -  p  -  n  -  -
 -  -  -  -  p  p  B  -
 -  -  -  -  -  -  -  -
 -  -  N  P  -  -  -  -
 P  P  P  -  P  P  P  P
 -  K  R  -  Q  B  N  R
```
