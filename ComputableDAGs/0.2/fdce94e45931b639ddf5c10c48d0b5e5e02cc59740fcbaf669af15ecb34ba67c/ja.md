```
DataTaskNode <: Node
```

データを転送し、計算を行わないノードです。

# フィールド

`.task`:            ノードのデータタスクタイプ。通常は [`DataTask`](@ref)。 `.parents`:         ノードの親のベクター（すなわち、このノードに依存するノード）。 `.children`:        ノードの子のタプルのベクター（すなわち、このノードに依存するノード）とそのインデックス、タスクに渡される結果の関数呼び出しにおける順序を示します。 `.id`:              ノードのID。比較の速度を向上させ、一意の識別子として使用されます。 `.node_reduction`:  このノードの [`NodeReduction`](@ref) または `missing`、存在しない場合。最大で1つのみ存在できます。 `.node_split`:      このノードの [`NodeSplit`](@ref) または `missing`、存在しない場合。最大で1つのみ存在できます。 `.name`:            グラフへのエントリノードのためのこのノードの名前 ([`is_entry_node`](@ref))、実行時に入力を正しいノードに確実に割り当てるため。
