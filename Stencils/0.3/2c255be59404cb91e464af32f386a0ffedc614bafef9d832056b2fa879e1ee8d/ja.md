```
Positional <: AbstractPositionalStencil

Positional(offsets::Tuple{Vararg{Int}}...)
Positional(offsets::Tuple{Tuple{Vararg{Int}}})
Positional{O}()
```

任意の形状を持つステンシルで、中央点からの行/列の距離（正および負）を `Tuple{Int,Int}` で指定します。

ステンシルの半径は最も遠い座標から計算され、ステンシルの次元数 `N` は最初の座標の長さから取得されます。例えば、`1`、`2`、または `3` です。

名前付きオフセットを持つ類似のステンシルについては [`NamedStencil`](@ref) を参照してください。

## 例

```julia
julia> p = Positional((0, -1), (2, 1), (-1, 1), (0, 1)) 
Positional{((0, -1), (2, 1), (-1, 1), (0, 1)), 2, 2, 4, Nothing}
   ▄ 
 ▀ ▀ 
   ▀ 
```
