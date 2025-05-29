```
@domoves(board, moves...)
```

一連の手を使って `board` を更新し、新しいボードを返すマクロです。

キャスリングの手は、Julia のパーサーを満たすためにハイフンなしで示す必要があります（つまり、「OO」または「OOO」）。

# 例

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
