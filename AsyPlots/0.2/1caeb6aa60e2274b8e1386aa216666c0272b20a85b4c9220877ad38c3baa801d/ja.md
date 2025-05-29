```
Point2D(x::Real,y::Real; label="",pen=Pen())
Point2D(P; label="",pen=Pen())
```

二次元ポイントを表すグラフィックスプリミティブです。

`P` は実数の2タプル、`Vec2`、または `Complex` である可能性があります。

# 例

```julia-repl
julia> Point2D(3,-1;pen="DarkGreen")
Point2D(3,-1;pen=DarkGreen)
```
