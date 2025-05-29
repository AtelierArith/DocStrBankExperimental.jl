```
onlyfirst(ss::SquareSet)
```

最初の正方形を除いたすべての正方形を持つ正方形セットを返します。

# 例

```julia-repl
julia> onlyfirst(SquareSet(SQ_A4, SQ_D5, SQ_F6)) == SquareSet(SQ_A4)
true
```
