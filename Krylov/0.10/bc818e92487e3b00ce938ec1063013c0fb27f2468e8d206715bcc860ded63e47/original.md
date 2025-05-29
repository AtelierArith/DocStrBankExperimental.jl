Workspace for the in-place method [`lslq!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = LslqWorkspace(m, n, S)
workspace = LslqWorkspace(A, b)
workspace = LslqWorkspace(kc::KrylovConstructor)
```
