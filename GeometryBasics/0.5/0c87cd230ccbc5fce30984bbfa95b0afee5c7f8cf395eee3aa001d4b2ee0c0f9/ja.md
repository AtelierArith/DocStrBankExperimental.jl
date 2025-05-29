```
Point{N, T}(args...)
Point{N, T}(args::Union{AbstractVector, Tuple, NTuple, StaticVector})
```

与えられた引数から長さ `N` の Point を構築します。

Point と Vec は厳密な数学的定義に従っていないことに注意してください。代わりに、これらを互換的に使用できるようにしています。

## エイリアス

|     |          `T` |   `Float64` |   `Float32` |       `Int` |       `UInt` |
| ---:| ------------:| -----------:| -----------:| -----------:| ------------:|
| `N` | `Point{N,T}` | `Pointd{N}` | `Pointf{N}` | `Pointi{N}` | `Pointui{N}` |
| `2` |  `Point2{T}` |   `Point2d` |   `Point2f` |   `Point2i` |   `Point2ui` |
| `3` |  `Point3{T}` |   `Point3d` |   `Point3f` |   `Point3i` |   `Point3ui` |
