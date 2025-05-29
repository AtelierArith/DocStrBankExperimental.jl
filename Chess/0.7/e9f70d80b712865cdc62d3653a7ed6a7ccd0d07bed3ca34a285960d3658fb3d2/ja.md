```
issingleton(ss::SquareSet)
```

`ss`が正方形を1つだけ含んでいるかどうかを判断します。

# 例

```julia-repl
julia> issingleton(SquareSet(SQ_D5))
true

julia> issingleton(SquareSet(SQ_D5, SQ_C5))
false

julia> issingleton(SS_EMPTY)
false
```
