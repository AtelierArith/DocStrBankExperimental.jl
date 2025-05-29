```
rule1(point1::Point, point2::Point;
    boundingbox=BoundingBox(),
    vertices=false)
```

点 `point1` と `point2` を通る直線を描きます。

```julia
rule(Point(10, 10), Point(30, -30))
```

境界ボックスを指定して、ルールラインを矩形領域に制限します。

2つの端点をベクターで返します。

`vertices=true` を使用すると、線を描かずに端点のみを返します。
