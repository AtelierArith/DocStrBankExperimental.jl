```
@private mem = 1
```

Creates a private local of `mem` per item in the workgroup. This can be safely used across [`@synchronize`](@ref) statements.
