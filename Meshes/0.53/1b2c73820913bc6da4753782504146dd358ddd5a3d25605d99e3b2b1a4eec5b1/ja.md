```
GridTopology(dims, [periodic])
```

`dims` 要素を持つグリッドトポロジーのデータ構造。オプションで、どの次元が `periodic` であるかを指定します。デフォルトは非周期的次元です。

## 例

```julia
julia> GridTopology((10,20)) # グリッド内の10x20要素
julia> GridTopology((10,20), (true,false)) # シリンダートポロジー
```
