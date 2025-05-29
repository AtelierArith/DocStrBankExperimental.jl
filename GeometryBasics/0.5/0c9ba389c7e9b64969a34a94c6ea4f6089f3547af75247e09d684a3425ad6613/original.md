```
Mat{R, C, T[, L]}(args::Union{UniformScaling, Tuple, AbstractMatrix})
Mat{R, C}(args::Union{Tuple, AbstractMatrix})
Mat{C}(args::Tuple)
```

Constructs a static Matrix from the given inputs. Can also take multiple numeric args. If only one size is given the matrix is assumed to be square.

### Aliases

|     |        `T` | `Float64` | `Float32` |     `Int` |     `UInt` |
| ---:| ----------:| ---------:| ---------:| ---------:| ----------:|
| `N` | `Mat{N,T}` | `Matd{N}` | `Matf{N}` | `Mati{N}` | `Matui{N}` |
| `2` |  `Mat2{T}` |   `Mat2d` |   `Mat2f` |   `Mat2i` |   `Mat2ui` |
| `3` |  `Mat3{T}` |   `Mat3d` |   `Mat3f` |   `Mat3i` |   `Mat3ui` |
