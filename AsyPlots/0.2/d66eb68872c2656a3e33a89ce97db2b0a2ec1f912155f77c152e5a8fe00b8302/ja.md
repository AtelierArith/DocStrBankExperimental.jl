```
Path2D(points;label="",pen=Pen(),arrow=NoArrow(),spline=false)
Path2D(x,y;label="",pen=Pen(),arrow=NoArrow(),spline=false)
```

二次元パスを表すグラフィックスプリミティブ

`points` は `Vec2` の配列、2タプルの配列、または $n × 2$ 配列であることができます。あるいは、座標のイテラブルを `x` と `y` として別々に提供することもできます。

# 例

```julia-repl
julia> Path2D([(0,0),(1,0),(1,1)];pen="MidnightBlue")
Path2D(<3 points>;pen=MidnightBlue)
```
