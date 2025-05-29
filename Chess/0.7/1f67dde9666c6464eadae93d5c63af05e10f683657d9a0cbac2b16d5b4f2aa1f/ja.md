```
flip(b::Board)
```

同一のボードを返しますが、垂直に反転され、動かす側が逆になります。

# 例

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

julia> flip(b)
Board (r1bqkbnr/pp3ppp/2n1p3/1Bpp4/8/4PN2/PPPP1PPP/RNBQ1RK1 b kq -):
 r  -  b  q  k  b  n  r
 p  p  -  -  -  p  p  p
 -  -  n  -  p  -  -  -
 -  B  p  p  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  P  N  -  -
 P  P  P  P  -  P  P  P
 R  N  B  Q  -  R  K  -
```
