```
update_storage!(a::AbstractStateAction, amp::AbstractManoptProblem, s::AbstractManoptSolverState)
```

[`AbstractStateAction`](@ref) `a` の内部値を [`AbstractManoptSolverState`](@ref) `s` に与えられた値に更新します。`amp` からの情報を使用して最適化されます。
