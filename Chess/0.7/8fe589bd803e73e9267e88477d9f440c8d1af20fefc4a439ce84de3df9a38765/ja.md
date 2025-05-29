```
isok(c::PieceColor)
```

`PieceColor` の値が有効かどうかをテストします。

`c` が `WHITE` または `BLACK` のいずれかである場合にのみ `true` を返します。

# 例

```julia-repl
julia> isok(WHITE)
true

julia> isok(BLACK)
true

julia> isok(COLOR_NONE)
false

julia> isok(PieceColor(42))
false
```
