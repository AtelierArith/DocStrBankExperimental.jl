```
const Rect{N,T} = HyperRectangle{N,T}
```

A rectangle in N dimensions, formally the Cartesian product of intervals. See also [`HyperRectangle`](@ref). Its aliases are

|          | `T`(eltype) |  `Float64` |  `Float32` |      `Int` |
| --------:| -----------:| ----------:| ----------:| ----------:|
| `N`(dim) | `Rect{N,T}` | `Rectd{N}` | `Rectf{N}` | `Recti{N}` |
|      `2` |  `Rect2{T}` |   `Rect2d` |   `Rect2f` |   `Rect2i` |
|      `3` |  `Rect3{T}` |   `Rect3d` |   `Rect3f` |   `Rect3i` |

There is an additional unexported alias `RectT` that simply reverses the order of type parameters: `RectT{T,N} == Rect{N,T}`.
