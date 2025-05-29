```
heuristic_leftmost(node::AbstractRuleNode, max_depth::Int)::Union{ExpandFailureReason, HoleReference}
```

穴に対するヒューリスティックを定義し、最も左の穴が常に最初に考慮されます。穴が見つかると[`HoleReference`](@ref)を返します。これは列挙子のデフォルトオプションです。
