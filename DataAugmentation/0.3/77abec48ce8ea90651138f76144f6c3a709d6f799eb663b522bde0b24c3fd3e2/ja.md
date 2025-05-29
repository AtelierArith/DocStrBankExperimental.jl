```
Polygon(points, sz)
Polygon{N, T, M}(points, bounds)
```

[`Keypoints`](@ref) のアイテムラッパー。

## 例

{cell=Polygon}

```julia
using DataAugmentation, StaticArrays
points = [SVector(10., 10.), SVector(80., 20.), SVector(90., 70.), SVector(20., 90.)]
item = Polygon(points, (100, 100))
```

{cell=Polygon}

```julia
showitems(item)
```
