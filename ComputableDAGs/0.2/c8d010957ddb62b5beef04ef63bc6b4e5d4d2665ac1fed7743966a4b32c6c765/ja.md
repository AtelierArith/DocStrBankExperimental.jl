```
optimize_step!(optimizer::AbstractOptimizer, graph::DAG)
```

[`AbstractOptimizer`](@ref) の実装によって実装されなければならないインターフェース関数です。操作が適用された場合は `true` を返し、適用されなかった場合は `false` を返します。通常、これはアルゴリズムの不変点に達したときです。

与えられた [`DAG`](@ref) に対して最小の論理ステップを1つ実行し、グラフを変更し、必要に応じてオプティマイザの状態も変更する必要があります。
