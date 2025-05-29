```
isrequired = lines_required(obj::GlobalRef, src::CodeInfo, edges::CodeEdges)
isrequired = lines_required(idx::Int,                     src::CodeInfo, edges::CodeEdges)
```

Determine which lines might need to be executed to evaluate `obj` or the statement indexed by `idx`. If `isrequired[i]` is `false`, the `i`th statement is *not* required. In some circumstances all statements marked `true` may be needed, in others control-flow will end up skipping a subset of such statements, perhaps while repeating others multiple times.

See also [`lines_required!`](@ref) and [`selective_eval!`](@ref).
