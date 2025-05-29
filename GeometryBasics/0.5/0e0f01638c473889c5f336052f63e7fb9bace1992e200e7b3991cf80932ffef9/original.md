```
Vec{N, T}(args...)
Vec{N, T}(args::Union{AbstractVector, Tuple, NTuple, StaticVector})
```

Constructs a Vec of length `N` from the given arguments.

Note that Point and Vec don't follow strict mathematical definitions. Instead we allow them to be used interchangeably.

## Aliases

|     |        `T` | `Float64` | `Float32` |     `Int` |     `UInt` |
| ---:| ----------:| ---------:| ---------:| ---------:| ----------:|
| `N` | `Vec{N,T}` | `Vecd{N}` | `Vecf{N}` | `Veci{N}` | `Vecui{N}` |
| `2` |  `Vec2{T}` |   `Vec2d` |   `Vec2f` |   `Vec2i` |   `Vec2ui` |
| `3` |  `Vec3{T}` |   `Vec3d` |   `Vec3f` |   `Vec3i` |   `Vec3ui` |
