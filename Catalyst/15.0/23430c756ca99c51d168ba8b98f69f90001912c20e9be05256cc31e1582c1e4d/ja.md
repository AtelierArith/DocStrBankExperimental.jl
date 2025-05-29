```
ModelingToolkit.flatten(rs::ReactionSystem)
```

与えられた [`ReactionSystem`](@ref) のすべてのサブシステムを `rs` に統合します。

注意:

  * フラット化されたシステムを表す新しい `ReactionSystem` を返します。
  * サブシステム内のすべての `Reaction` は名前空間化され、`rs` の `Reactions` のリストに統合されます。統合されたリストは `reactions(rs)` として利用可能です。
  * すべての代数方程式と微分方程式は `rs` の方程式に統合されます。
  * 現在、フラット化の際にサブシステムとしてサポートされているのは `ReactionSystem`、`NonlinearSystem`、および `ODESystem` のみです。
  * フラット化時に `rs.networkproperties` はリセットされます。
  * `combinatoric_ratelaws` のデフォルト値はすべての `ReactionSystem` の論理和になります。
