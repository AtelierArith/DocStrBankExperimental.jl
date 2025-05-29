```
queens(b::Board)
```

クイーンのいずれかの色を含むマスの集合。

# 例

```julia-repl
julia> b = startboard();

julia> queens(b) == SquareSet(SQ_D1, SQ_D8)
true
```
