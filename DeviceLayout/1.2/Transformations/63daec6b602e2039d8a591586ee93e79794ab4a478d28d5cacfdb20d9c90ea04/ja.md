```
origin(f::Transformation)
```

変換された原点を返します。もし変換が行われていない場合は `nothing` を返します。

変換が行われていない場合は `zero(Point{T})` ではなく `nothing` を返す必要があります。なぜなら、そのような変換（例：`LinearMap`）は座標型 `T` を提供しない可能性があるからです。
