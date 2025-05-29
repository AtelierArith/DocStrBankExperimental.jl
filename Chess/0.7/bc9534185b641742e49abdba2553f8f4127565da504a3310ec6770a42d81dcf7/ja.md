```
isattacked(b::Board, s::Square, side::PieceColor)
```

与えられたマスが指定された側によって攻撃されているかどうかを判断します。

# 例

```julia-repl
julia> b = startboard();

julia> isattacked(b, SQ_F3, WHITE)
true

julia> isattacked(b, SQ_F3, BLACK)
false
```
