```
MBQCResourceState(graph, flow, angles)
```

MBQCにおけるリソース状態を表す構造体。

# パラメータ

  * `graph`: 基本的なグラフ構造を表す`MBQCGraph`のインスタンス。
  * `flow`: リソース状態におけるフローを表す`MBQCFlow`のインスタンス。
  * `angles`: 各頂点に関連付けられた角度を表す`MBQCAngles`のインスタンス。

## 例

```julia
# MBQCGraphを作成
graph = MBQCGraph([1, 2, 3], [(1, 2), (2, 3)])

# MBQCFlowを作成
flow = MBQCFlow((1, 2) => 2, (2, 3) => 3)

# MBQCAnglesを作成
angles = MBQCAngles([π/2, π/4, π/3])

# MBQCResourceStateを作成
resource_state = MBQCResourceState(graph, flow, angles)
```
