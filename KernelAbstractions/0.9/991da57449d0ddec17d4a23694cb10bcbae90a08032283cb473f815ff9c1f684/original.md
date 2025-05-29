```
@private T dims
```

Declare storage that is local to each item in the workgroup. This can be safely used across [`@synchronize`](@ref) statements. On a CPU, this will allocate additional implicit dimensions to ensure correct localization.

For storage that only persists between `@synchronize` statements, an `MArray` can be used instead.

See also [`@uniform`](@ref).
