```
domove!(b::Board, m::Move)
domove!(b::Board, m::String)
```

Destructively modify the board `b` by making the move `m`.

If the supplied move is a string, this function tries to parse the move as a UCI move first, then as a SAN move.

It's the caller's responsibility to make sure the move `m` is legal.

The function returns a value of type `UndoInfo`. You'll need this if you want to later call `undomove!()` to take back the move and get the original position back.

# Examples

```julia-repl
julia> b = startboard();

julia> domove!(b, "d4");

julia> b
Board (rnbqkbnr/pppppppp/8/8/3P4/8/PPP1PPPP/RNBQKBNR b KQkq -):
 r  n  b  q  k  b  n  r
 p  p  p  p  p  p  p  p
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  P  -  -  -  -
 -  -  -  -  -  -  -  -
 P  P  P  -  P  P  P  P
 R  N  B  Q  K  B  N  R
```
