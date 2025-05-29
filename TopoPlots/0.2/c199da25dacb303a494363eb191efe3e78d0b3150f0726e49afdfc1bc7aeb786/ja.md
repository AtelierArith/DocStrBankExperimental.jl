```
GeomExtrapolation(
    method = Shepard(), # 外挿法
    geometry = Rect, # 点の周りにフィットさせる幾何学
    enlarge = 3.0 # 追加の点を加えるために境界幾何学を拡大する量
)
```

位置とデータを取り、拡大された境界幾何学上の点と追加のデータポイントを返します：

```julia
extra = GeomExtrapolation()
extra_positions, extra_data, bounding_geometry, bounding_geometry_enlarged = extra(positions, data)
```
