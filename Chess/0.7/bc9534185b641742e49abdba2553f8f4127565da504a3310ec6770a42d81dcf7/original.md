```
isattacked(b::Board, s::Square, side::PieceColor)
```

Determine whether the given square is attacked by the given side.

# Examples

```julia-repl
julia> b = startboard();

julia> isattacked(b, SQ_F3, WHITE)
true

julia> isattacked(b, SQ_F3, BLACK)
false
```
