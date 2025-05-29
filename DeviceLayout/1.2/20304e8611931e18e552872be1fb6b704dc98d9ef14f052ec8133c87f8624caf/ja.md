```
compass(;p0=Point(0μm, 0μm))
```

`p0`にある`PointHook`の8方向コンパス。

すべての方位および主要な中間方位（45°ごと）のための`NamedTuple` `(:east = PointHook(p0, 0°), :northeast = PointHook(p0, 45°), ...`。（各フックの`in_direction`はそのコンパスの方向を指します。）
