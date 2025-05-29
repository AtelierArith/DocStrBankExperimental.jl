```
fix([context::AbstractContext,] values::NamedTuple)
fix([context::AbstractContext]; values...)
```

Return `FixedContext` with `values` and `context` if `values` is non-empty, otherwise return `context` which is [`DefaultContext`](@ref) by default.

See also: [`unfix`](@ref)
