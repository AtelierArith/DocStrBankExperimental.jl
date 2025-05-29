```
is_flippable(g::TriangulatedPolygon, src::Integer, dst::Integer) :: Bool
```

エッジがフリップ可能かどうかを返します。

凸多角形の三角形分割において、内側のエッジは常にフリップ可能ですが、外側のエッジはフリップできません。
