```
planarize!(nodes, plane = :XY)
```

ノードのセットの自由度（DOF）を指定されたグローバル平面に制限します。例えば、2D構造を分析する際に使用します。

# 引数

  * `nodes::Vector{<:AbstractNode}` 制限するノードのベクター
  * `plane::Symbol = :XY` DOFを制限する平面。デフォルトはXY平面で、次のいずれかを指定できます：

      * :XY
      * :XZ
      * :YZ
