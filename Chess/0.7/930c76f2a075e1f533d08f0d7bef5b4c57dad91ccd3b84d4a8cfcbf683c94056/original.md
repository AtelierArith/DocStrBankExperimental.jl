```
undomove!(b::Board, u::UndoInfo)
```

Undo a move earlier done by `domove!()`.

The second parameter is the `UndoInfo` value returned by the earlier call to `domove!()`.

# Examples

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
