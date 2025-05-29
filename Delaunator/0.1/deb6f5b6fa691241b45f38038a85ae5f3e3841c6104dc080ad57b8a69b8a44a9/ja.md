```
hullpoly(t)
```

凸包の座標を返し、ポリゴンとしてプロットするのに適しています。

# 例

```
t = triangulate(rand(StableRNG(1), Point2f, 10))
f = scatter(t.points)
poly!(f.axis,collect(hullpoly(t)),color=:transparent, strokewidth=1)
f
```
