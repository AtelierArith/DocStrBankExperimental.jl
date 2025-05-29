```
is_valid(shape)
```

`shape`が描画可能な有効な形状であれば`true`を返し、そうでなければ`false`を返します。

# 例

```julia-repl
julia> is_valid(Rectangle(Point(9, 5), 16, 24))
true

julia> is_valid(Rectangle(Point(9, 5), -16, 24))
false
```
