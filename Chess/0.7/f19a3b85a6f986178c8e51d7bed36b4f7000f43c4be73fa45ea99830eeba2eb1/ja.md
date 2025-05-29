```
isok(r::SquareRank)
```

`SquareRank`が有効な値を含んでいるかどうかをテストします。

# 例

```julia-repl
julia> isok(RANK_6)
true

julia> isok(SquareRank(42))
false
```
