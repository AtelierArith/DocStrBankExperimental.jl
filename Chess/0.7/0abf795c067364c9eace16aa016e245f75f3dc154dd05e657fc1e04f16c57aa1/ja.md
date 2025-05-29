```
removefirst(ss::SquareSet)
```

正方形セットの最初のメンバーを削除します。

# 例

```julia-repl
julia> removefirst(SquareSet(SQ_A4, SQ_D5, SQ_F6)) == SquareSet(SQ_D5, SQ_F6)
true
```
