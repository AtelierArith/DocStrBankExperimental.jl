```
Keypoints(points, sz)
Keypoints{N, T, M}(points, bounds)
```

`N`次元のキーポイントは`SVector{N, T}`として表されます。

空間的境界は、ポリゴン`bounds::Vector{SVector{N, T}}`または`sz::NTuple{N, Int}`によって与えられます。

## 例

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
