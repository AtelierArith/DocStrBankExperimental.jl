EquilateralTriangleGridは、`side`の辺の長さを持つ等辺三角形のグリッドを作成するイテレータで、`nrows`と`ncols`の矩形グリッド上に配置されます。

```julia
EquilateralTriangleGrid(startpoint::Point, side, nrows, ncols; up = true)
```

最初の三角形は`startpoint`を中心に配置され、`up`がtrueの場合は上を向きます。

###例

```julia
nrows = 5
ncols = 8
side = 150
eqtg = EquilateralTriangleGrid(O, side, nrows, ncols)

@show first(eqtg)
# (Point[Point(-75.0, 64.9519052838329), 
         Point(0.0, -64.9519052838329), 
         Point(75.0, 64.9519052838329)], 1)

# これでイテレータを使って三角形を生成（および描画）できます：
for tri in eqtg
    vertices, trianglenumber = tri
    randomhue()
    poly(vertices, :fill)
end
```
