```
condition([context::AbstractContext,] values::NamedTuple)
condition([context::AbstractContext]; values...)
```

Return `ConditionContext` with `values` and `context` if `values` is non-empty, otherwise return `context` which is [`DefaultContext`](@ref) by default.

See also: [`decondition`](@ref)
