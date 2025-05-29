```
domoves!(b::Board, moves::Vararg{Move})
domoves!(b::Board, moves::Vararg{String}; movelist::MoveList = MoveList(200))
```

Destructively modify the board b by making a sequence of moves.

If the supplied moves are strings, this function tries to parse the moves as UCI moves first, and as SAN moves if UCI move parsing fails.

It's the caller's responsibility to make sure all moves are legal. If a plain move is illegal, the consequences are undefined. If a move string cannot be parsed as an unambiguous legal move, the function throws an exception.

In the `move::Vararg{String}` case, `movefromsan` is called. This can be supplied a pre-allocated `MoveList` in order to save time/space due to unnecessary allocations. If provided, the `movelist` parameter will be passed to `movefromsan`. It is up to the caller to ensure that `movelist` has sufficient capacity.

There is also a non-destructive version of this version, named `domoves`.

# Examples

```julia-repl
julia> b = startboard();

julia> domoves!(b, "e4", "c5", "Nf3", "d6", "d4", "cxd4", "Nxd4", "Nf6", "Nc3");

julia> b
Board (rnbqkb1r/pp2pppp/3p1n2/8/3NP3/2N5/PPP2PPP/R1BQKB1R b KQkq -):
 r  n  b  q  k  b  -  r
 p  p  -  -  p  p  p  p
 -  -  -  p  -  n  -  -
 -  -  -  -  -  -  -  -
 -  -  -  N  P  -  -  -
 -  -  N  -  -  -  -  -
 P  P  P  -  -  P  P  P
 R  -  B  Q  K  B  -  R

julia> b = startboard();

julia> domoves!(b, "e4", "Qxe4+")
ERROR: "Illegal or ambiguous move: Qxe4+"
```
