```
heuristic_random(node::AbstractRuleNode, max_depth::Int)::Union{ExpandFailureReason, HoleReference}
```

穴に対するヒューリスティックを定義し、ランダムな探索を使用してランダムに穴を選択します。穴が見つかると、[`HoleReference`](@ref)を返します。
