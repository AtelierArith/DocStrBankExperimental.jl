```
FDMnode(x::Real, y::Real, z::Real, dof::Bool, id = :node)
FDMnode(pos::Vector{<:Real}, dof::Bool, id = :node)
```

FDMネットワーク内のノードは、その空間的位置[x, y, z]と自由度（自由 = `true`、固定 = `false`）によって定義されます。

# フィールド

  * position::Vector{Float64}: ノードの[x,y,z]位置
  * dof::Bool: true = 自由; false = 固定
  * id::Symbol: 識別子（オプション）
  * nodeID::Integer: グローバル識別子（内部）
  * reaction::Vector{Float64}: ノードが固定されている場合の[x,y,z]反力
