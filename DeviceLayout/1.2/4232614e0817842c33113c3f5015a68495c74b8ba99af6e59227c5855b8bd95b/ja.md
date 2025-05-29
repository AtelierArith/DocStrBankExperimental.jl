```
centered(ent::AbstractGeometry; on_pt=zero(Point{T}))
```

`ent`のコピーを`on_pt`に中心を合わせて配置します。必要に応じて座標が昇格されます。この関数は、`ent`が整数座標を持っていても`InexactError()`をスローしません。
