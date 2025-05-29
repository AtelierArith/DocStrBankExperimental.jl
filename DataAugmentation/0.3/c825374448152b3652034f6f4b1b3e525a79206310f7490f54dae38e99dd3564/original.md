```
Keypoints(points, sz)
Keypoints{N, T, M}(points, bounds)
```

`N`-dimensional keypoints represented as `SVector{N, T}`.

Spatial bounds are given by the polygon `bounds::Vector{SVector{N, T}}` or `sz::NTuple{N, Int}`.

## Examples

{cell=Keypoints}

```julia
using DataAugmentation, StaticArrays
points = [SVector(y, x) for (y, x) in zip(4:5:80, 10:6:90)]
item = Keypoints(points, (100, 100))
```

{cell=Keypoints}

```julia
showitems(item)
```
