```
const Rect{N,T} = HyperRectangle{N,T}
```

N次元の長方形で、形式的には区間のデカルト積です。詳細は[`HyperRectangle`](@ref)を参照してください。エイリアスは次の通りです。

|          | `T`(eltype) |  `Float64` |  `Float32` |      `Int` |
| --------:| -----------:| ----------:| ----------:| ----------:|
| `N`(dim) | `Rect{N,T}` | `Rectd{N}` | `Rectf{N}` | `Recti{N}` |
|      `2` |  `Rect2{T}` |   `Rect2d` |   `Rect2f` |   `Rect2i` |
|      `3` |  `Rect3{T}` |   `Rect3d` |   `Rect3f` |   `Rect3i` |

追加のエクスポートされていないエイリアス`RectT`があり、これは単に型パラメータの順序を逆にします：`RectT{T,N} == Rect{N,T}`。
