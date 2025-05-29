```
heuristic_smallest_domain(node::AbstractRuleNode, max_depth::Int)::Union{ExpandFailureReason, HoleReference}
```

未完成のAST内のすべての利用可能な穴に対して、各ドメインのサイズを考慮することでヒューリスティックを定義します。ここでのドメインは、制約に関して可能な導出の数を説明します。穴が見つかると、[`HoleReference`](@ref)を返します。
