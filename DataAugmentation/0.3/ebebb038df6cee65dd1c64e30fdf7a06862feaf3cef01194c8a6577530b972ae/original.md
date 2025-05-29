```
BoundingBox(points, sz)
BoundingBox{N, T, M}(points, bounds)
```

Item wrapper around [`Keypoints`](@ref).

## Examples

{cell=BoundingBox}

```julia
using DataAugmentation, StaticArrays
points = [SVector(10., 10.), SVector(80., 60.)]
item = BoundingBox(points, (100, 100))
```

{cell=BoundingBox}

```julia
showitems(item)
```
