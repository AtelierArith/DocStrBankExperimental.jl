```
domoves(b::Board, moves::Vararg{Move})
domoves(b::Board, moves::Vararg{String}; movelist::MoveList = MoveList(200))
```

Return the board achieved from a starting board `b` by making a sequence of moves.

The input board `b` is left unchanged.

If the supplied moves are strings, this function tries to parse the moves as UCI moves first, and as SAN moves if UCI move parsing fails.

It's the caller's responsibility to make sure all moves are legal. If a plain move is illegal, the consequences are undefined. If a move string cannot be parsed as an unambiguous legal move, the function throws an exception.

In the `move::Vararg{String}` case, `movefromsan` is called. This can be supplied a pre-allocated `MoveList` in order to save time/space due to unnecessary allocations. If provided, the `movelist` parameter will be passed to `movefromsan`. It is up to the caller to ensure that `movelist` has sufficient capacity.

There is also a destructive version of this version, named `domoves!`

# Examples

```julia-repl
julia> b = startboard();

julia> domoves(b, "d4", "Nf6", "c4", "e6", "Nc3", "Bb4")
Board (rnbqk2r/pppp1ppp/4pn2/8/1bPP4/2N5/PP2PPPP/R1BQKBNR w KQkq -):
 r  n  b  q  k  -  -  r
 p  p  p  p  -  p  p  p
 -  -  -  -  p  n  -  -
 -  -  -  -  -  -  -  -
 -  b  P  P  -  -  -  -
 -  -  N  -  -  -  -  -
 P  P  -  -  P  P  P  P
 R  -  B  Q  K  B  N  R

julia> movelist = MoveList(200)
0-element MoveList

julia> domoves(b, "d4", "Nf6", "c4", "e6", "Nc3", "Bb4"; movelist=movelist)
Board (rnbqk2r/pppp1ppp/4pn2/8/1bPP4/2N5/PP2PPPP/R1BQKBNR w KQkq -):
 r  n  b  q  k  -  -  r
 p  p  p  p  -  p  p  p
 -  -  -  -  p  n  -  -
 -  -  -  -  -  -  -  -
 -  b  P  P  -  -  -  -
 -  -  N  -  -  -  -  -
 P  P  -  -  P  P  P  P
 R  -  B  Q  K  B  N  R

julia> domoves(b, "d4", "Nf6", "c5")
ERROR: "Illegal or ambiguous move: c5"
```
