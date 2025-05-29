```
Polygon2D(points;pen=Pen(),
                 fillpen=Pen(color="white"),
                 spline=false)
```

2次元ポリゴンを表すグラフィックスプリミティブ

`points` は `Vec2` の配列、2タプルの配列、または $n × 2$ 配列であることができます。あるいは、座標のイテラブルを `x` と `y` として別々に提供することもできます。

# 例

```julia-repl
julia> Polygon2D([(0,0),(1,0),(1,1)];pen="MidnightBlue")
Polygon2D(<3 points>;pen=MidnightBlue)
```
