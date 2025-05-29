```
Square
```

Type representing a square on a chess board.

A `Square` can be constructed either with an `Int` (with the convention a8=1, a7=2, ..., a1=8, b8=9, b7=10, ..., h1=64) or with a `SquareFile` and a `SquareRank`. There are also constants `SQ_A1`, ..., `SQ_H8` for all 64 squares on the board.

# Examples

```julia-repl
julia> Square(FILE_G, RANK_6)
SQ_G6

julia> Square(8)
SQ_A1
```
