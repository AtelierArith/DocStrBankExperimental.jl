```
@ismatch value pattern
```

`value`が`pattern`に一致する場合は`true`を返し、一致しない場合は`false`を返します。`true`を返すときは、パターン変数を囲むスコープにバインドします。

パターンの構文については、`@match`も参照してください。

# 例

```julia-repl
julia> struct Point
            x
            y
        end

julia> p = Point(0, 3)
Point(0, 3)

julia> if @ismatch p Point(0, y)
            println("y軸上のy = ", y)
        end
y軸上のy = 3
```

ガード付きパターンは`@ismatch`と一緒に使用すべきではありません。代わりに`&&`を使用できます：

```julia-repl
julia> if (@ismatch p Point(x, y)) && x < y
            println("点 (", x, ", ", y, ") は上左半平面にあります")
        end
点 (0, 3) は上左半平面にあります
```
