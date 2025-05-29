```
isok(s::Square)
```

`Square`が有効な値を持っているかどうかをテストします。

# 例

```julia-repl
julia> isok(SQ_G7)
true

julia> isok(Square(42))
true

julia> isok(Square(100))
false

julia> isok(Square(0))
false
```
