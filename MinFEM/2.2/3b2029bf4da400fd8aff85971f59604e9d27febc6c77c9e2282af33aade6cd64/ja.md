```julia
mutable struct Domain <: MinFEM.Region
```

特定の物理ドメインの名前と要素インデックスのセットを保持する型です。

# フィールド

  * `Name::String`: 一意の物理名
  * `Nodes::Set{Int64}`: ノードインデックスのリスト
  * `Elements::Set{Int64}`: 要素インデックスのリスト
