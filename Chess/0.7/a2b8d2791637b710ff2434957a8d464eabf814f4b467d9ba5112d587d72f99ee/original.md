```
@domoves!(board, moves...)
```

A macro for destructively updating `board` with a sequence of moves.

Castling moves must be indicated without a hyphen (i.e. "OO" or "OOO") in order to satisfy Julia's parser.

# Examples

```
julia> b = @startboard Nf3 Nf6;

julia> @domoves b g3 g6;

julia> b
Board (rnbqkb1r/pppppppp/5n2/8/8/5N2/PPPPPPPP/RNBQKB1R w KQkq -):
 r  n  b  q  k  b  -  r
 p  p  p  p  p  p  p  p
 -  -  -  -  -  n  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  N  -  -
 P  P  P  P  P  P  P  P
 R  N  B  Q  K  B  -  R
```
