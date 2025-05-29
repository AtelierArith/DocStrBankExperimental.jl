Workspace for the in-place method [`fgmres!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = FgmresWorkspace(m, n, S; memory = 20)
workspace = FgmresWorkspace(A, b; memory = 20)
workspace = FgmresWorkspace(kc::KrylovConstructor; memory = 20)
```

`memory` is set to `n` if the value given is larger than `n`.
