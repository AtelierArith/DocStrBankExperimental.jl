Workspace for the in-place method [`gmres!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = GmresWorkspace(m, n, S; memory = 20)
workspace = GmresWorkspace(A, b; memory = 20)
workspace = GmresWorkspace(kc::KrylovConstructor; memory = 20)
```

`memory` is set to `n` if the value given is larger than `n`.
