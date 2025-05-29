```
@domoves(board, moves...)
```

A macro for updating `board` with a sequence of moves, returning a new board.

Castling moves must be indicated without a hyphen (i.e. "OO" or "OOO") in order to satisfy Julia's parser.

# Examples

```julia-repl
julia> b = @startboard d4 d5;

julia> @domoves b c4 e6
Board (rnbqkbnr/ppp2ppp/4p3/3p4/2PP4/8/PP2PPPP/RNBQKBNR w KQkq -):
 r  n  b  q  k  b  n  r
 p  p  p  -  -  p  p  p
 -  -  -  -  p  -  -  -
 -  -  -  p  -  -  -  -
 -  -  P  P  -  -  -  -
 -  -  -  -  -  -  -  -
 P  P  -  -  P  P  P  P
 R  N  B  Q  K  B  N  R
```
