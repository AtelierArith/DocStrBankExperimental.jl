```
@domoves!(board, moves...)
```

一連の手を使って`board`を破壊的に更新するためのマクロです。

キャスリングの手は、ハイフンなしで示す必要があります（つまり、「OO」または「OOO」）ので、Juliaのパーサーを満たす必要があります。

# 例

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
