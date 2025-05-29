```
check_tree(c::ForbiddenSequence, tree::AbstractRuleNode; sequence_started=false)::Bool
```

与えられた [`AbstractRuleNode`](@ref) ツリーが [`ForbiddenSequence`](@ref) 制約に従っているかどうかを確認します。
