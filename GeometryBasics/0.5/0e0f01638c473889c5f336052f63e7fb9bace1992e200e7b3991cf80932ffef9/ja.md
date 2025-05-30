```
Vec{N, T}(args...)
Vec{N, T}(args::Union{AbstractVector, Tuple, NTuple, StaticVector})
```

与えられた引数から長さ `N` の Vec を構築します。

Point と Vec は厳密な数学的定義に従っていないことに注意してください。代わりに、これらを互換的に使用できるようにしています。

## エイリアス

|     |        `T` | `Float64` | `Float32` |     `Int` |     `UInt` |
| ---:| ----------:| ---------:| ---------:| ---------:| ----------:|
| `N` | `Vec{N,T}` | `Vecd{N}` | `Vecf{N}` | `Veci{N}` | `Vecui{N}` |
| `2` |  `Vec2{T}` |   `Vec2d` |   `Vec2f` |   `Vec2i` |   `Vec2ui` |
| `3` |  `Vec3{T}` |   `Vec3d` |   `Vec3f` |   `Vec3i` |   `Vec3ui` |
