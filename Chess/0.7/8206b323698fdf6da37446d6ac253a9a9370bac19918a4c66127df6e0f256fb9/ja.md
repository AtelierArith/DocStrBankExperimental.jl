```
pieceon(b::Board, s::Square)
pieceon(b::Board, f::SquareFile, r::SquareRank)
pieceon(b::Board, s::String)
```

与えられたボードの指定されたマスにある駒を見つけます。

# 例

```julia-repl
julia> b = startboard();

julia> pieceon(b, SQ_E1)
PIECE_WK

julia> pieceon(b, FILE_B, RANK_8)
PIECE_BN

julia> pieceon(b, SQ_B5)
EMPTY

julia> pieceon(b, "d8")
PIECE_BQ
```
