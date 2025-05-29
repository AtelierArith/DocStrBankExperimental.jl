```
Point{N, T}(args...)
Point{N, T}(args::Union{AbstractVector, Tuple, NTuple, StaticVector})
```

Constructs a Point of length `N` from the given arguments.

Note that Point and Vec don't follow strict mathematical definitions. Instead we allow them to be used interchangeably.

## Aliases

|     |          `T` |   `Float64` |   `Float32` |       `Int` |       `UInt` |
| ---:| ------------:| -----------:| -----------:| -----------:| ------------:|
| `N` | `Point{N,T}` | `Pointd{N}` | `Pointf{N}` | `Pointi{N}` | `Pointui{N}` |
| `2` |  `Point2{T}` |   `Point2d` |   `Point2f` |   `Point2i` |   `Point2ui` |
| `3` |  `Point3{T}` |   `Point3d` |   `Point3f` |   `Point3i` |   `Point3ui` |
