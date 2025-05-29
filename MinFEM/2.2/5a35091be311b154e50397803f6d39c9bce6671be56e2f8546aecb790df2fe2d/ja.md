```julia
mutable struct Boundary <: MinFEM.Region
```

特定の物理境界の名前とノードおよびエッジインデックスのセットを保持する構造体。

# フィールド

  * `Name::String`: 一意の物理名
  * `Nodes::Set{Int64}`: ノードインデックスのリスト
  * `Elements::Set{Int64}`: 要素インデックスのリスト
