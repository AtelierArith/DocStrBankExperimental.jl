```
Morphological(fun)
```

関数 `fun` によって与えられる形態変換で、幾何学または領域の座標を新しい座標にマッピングします（`coords -> newcoords`）。

## 例

```julia
ball = Ball((0, 0), 1)
ball |> Morphological(c -> Cartesian(c.x + c.y, c.y, c.x - c.y))

triangle = Triangle(Point(LatLon(0, 0)), Point(LatLon(0, 45)), Point(LatLon(45, 0)))
triangle |> Morphological(c -> LatLonAlt(c.lat, c.lon, 0.0m))
```

### 注意事項

デフォルトでは、多面体の頂点のみが変換され、多様体変換で発生する歪みは無視されます。この場合を処理するには、[`TransformedGeometry`](@ref) を使用してください。
