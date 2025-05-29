```
undomove!(b::Board, u::UndoInfo)
```

`domove!()`によって以前に行われた手を元に戻します。

第二のパラメータは、以前の`domove!()`の呼び出しによって返された`UndoInfo`の値です。

# 例

```julia-repl
julia> b = startboard();

julia> u = domove!(b, "c4");

julia> b
Board (rnbqkbnr/pppppppp/8/8/2P5/8/PP1PPPPP/RNBQKBNR b KQkq -):
 r  n  b  q  k  b  n  r
 p  p  p  p  p  p  p  p
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  P  -  -  -  -  -
 -  -  -  -  -  -  -  -
 P  P  -  P  P  P  P  P
 R  N  B  Q  K  B  N  R

julia> undomove!(b, u);

julia> b
Board (rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq -):
 r  n  b  q  k  b  n  r
 p  p  p  p  p  p  p  p
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 P  P  P  P  P  P  P  P
 R  N  B  Q  K  B  N  R
```
