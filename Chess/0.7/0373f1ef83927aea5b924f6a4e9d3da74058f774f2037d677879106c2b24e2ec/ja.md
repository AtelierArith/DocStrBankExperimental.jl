```
knights(b::Board)
```

ナイトのいずれかの色を持つマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> knights(b) == SquareSet(SQ_B1, SQ_G1, SQ_B8, SQ_G8)
true
```
