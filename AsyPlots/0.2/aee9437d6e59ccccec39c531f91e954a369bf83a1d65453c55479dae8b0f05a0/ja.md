```
Polygon3D(points;pen=Pen(),
                 fillpen=Pen(color="white"),
                 spline=false)
```

三次元ポリゴンを表すグラフィックスプリミティブ

`points` は `Vec3` の配列または 3-タプルの配列である可能性があります。

# 例

```julia-repl
julia> Polygon3D([(0,0,0),(1,0,0),(1,1,0)];pen="MidnightBlue")
```
