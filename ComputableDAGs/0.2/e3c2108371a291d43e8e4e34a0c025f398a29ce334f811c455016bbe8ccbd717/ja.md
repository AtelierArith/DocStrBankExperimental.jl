```
ComputeTaskNode <: Node
```

入力から結果を計算するノードは、[`AbstractComputeTask`](@ref)を使用します。

# フィールド

`.task`:            ノードの計算タスクの型。[`AbstractComputeTask`](@ref)の具体的なサブタイプ。 `.parents`:         ノードの親のベクター（すなわち、このノードに依存するノード）。 `.children`:        ノードの子のタプルのベクター（すなわち、このノードに依存するノード）とそのインデックス。[`AbstractComputeTask`](@ref)の引数を順序付けるために使用されます。 `.id`:              ノードのID。比較の速度を向上させ、一意の識別子として使用されます。 `.node_reduction`:  このノードの[`NodeReduction`](@ref)または`missing`、存在しない場合。最大で1つだけ存在できます。 `.node_split`:      このノードの[`NodeSplit`](@ref)または`missing`、存在しない場合。最大で1つだけ存在できます。 `.device`:          このノードが[`Scheduler`](@ref)によってスケジュールされたデバイス。
