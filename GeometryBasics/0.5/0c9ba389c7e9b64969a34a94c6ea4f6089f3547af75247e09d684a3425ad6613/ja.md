```
Mat{R, C, T[, L]}(args::Union{UniformScaling, Tuple, AbstractMatrix})
Mat{R, C}(args::Union{Tuple, AbstractMatrix})
Mat{C}(args::Tuple)
```

与えられた入力から静的行列を構築します。複数の数値引数を取ることもできます。サイズが1つだけ指定された場合、行列は正方形であると見なされます。

### エイリアス

|     |        `T` | `Float64` | `Float32` |     `Int` |     `UInt` |
| ---:| ----------:| ---------:| ---------:| ---------:| ----------:|
| `N` | `Mat{N,T}` | `Matd{N}` | `Matf{N}` | `Mati{N}` | `Matui{N}` |
| `2` |  `Mat2{T}` |   `Mat2d` |   `Mat2f` |   `Mat2i` |   `Mat2ui` |
| `3` |  `Mat3{T}` |   `Mat3d` |   `Mat3f` |   `Mat3i` |   `Mat3ui` |
