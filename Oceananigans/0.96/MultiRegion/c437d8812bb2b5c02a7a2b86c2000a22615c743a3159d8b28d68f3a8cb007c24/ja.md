```
MultiRegionGrid(global_grid; partition = XPartition(2),
                             devices = nothing,
                             validate = true)
```

`global_grid`を異なる領域に分割し、`devices`によって処理します。

# 位置引数

  * `global_grid`: 領域に分割されるグリッド。

# キーワード引数

  * `partition`: 必要なパーティショニング。実装されているパーティショニングは`XPartition`（$x$方向に沿った分割）と`YPartition`（$y$方向に沿った分割）です。
  * `devices`: メモリを割り当てるデバイス。`nothing`が提供される場合（デフォルト）、メモリは`CPU`に割り当てられます。`GPU`計算の場合、メモリを割り当てるためのGPUの総数または特定のGPUを指定することが可能です。デバイスの数は領域の数と一致する必要はありません。
  * `validate :: Boolean`: `devices`を検証するかどうか; デフォルト: `true`。

# 例

```@example multiregion
julia> using Oceananigans

julia> using Oceananigans.MultiRegion: MultiRegionGrid, XPartition

julia> grid = RectilinearGrid(size=(12, 12), extent=(1, 1), topology=(Bounded, Bounded, Flat));

julia> multi_region_grid = MultiRegionGrid(grid, partition = XPartition(4))
```
