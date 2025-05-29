```
@startboard
```

A macro for initializing a board from the initial position with some moves.

Castling moves must be indicated without a hyphen (i.e. "OO" or "OOO") in order to satisfy Julia's parser.

# Examples

```julia-repl
julia> @startboard e4 e5 Nf3 Nc6 Bb5 a6 Ba4 Nf6 OO
Board (r1bqkb1r/1ppp1ppp/p1n2n2/4p3/B3P3/5N2/PPPP1PPP/RNBQ1RK1 b kq -):
 r  -  b  q  k  b  -  r
 -  p  p  p  -  p  p  p
 p  -  n  -  -  n  -  -
 -  -  -  -  p  -  -  -
 B  -  -  -  P  -  -  -
 -  -  -  -  -  N  -  -
 P  P  P  P  -  P  P  P
 R  N  B  Q  -  R  K  -
```
