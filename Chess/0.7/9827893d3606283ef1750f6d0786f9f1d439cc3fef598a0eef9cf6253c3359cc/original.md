```
domove(b::Board, m::Move)
domove(b::Board, m::String)
```

Do the move `m` on the board `b`, and return the new board.

The board `b` itself is left unchanged, a new board is returned. There is a much faster destructive function `domove!()` that should be called instead when high performance is required.

If the supplied move is a string, this function tries to parse the move as a UCI move first, then as a SAN move.

It's the caller's responsibility to make sure `m` is a legal move on this board.

# Examples

```julia-repl
julia> b = startboard();

julia> domove(b, "Nf3")
Board (rnbqkbnr/pppppppp/8/8/8/5N2/PPPPPPPP/RNBQKB1R b KQkq -):
 r  n  b  q  k  b  n  r
 p  p  p  p  p  p  p  p
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  -  -  -
 -  -  -  -  -  N  -  -
 P  P  P  P  P  P  P  P
 R  N  B  Q  K  B  -  R
```
