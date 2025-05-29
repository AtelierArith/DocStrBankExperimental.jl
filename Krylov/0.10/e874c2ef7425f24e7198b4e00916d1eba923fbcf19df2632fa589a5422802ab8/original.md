Workspace for the in-place method [`dqgmres!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = DqgmresWorkspace(m, n, S; memory = 20)
workspace = DqgmresWorkspace(A, b; memory = 20)
workspace = DqgmresWorkspace(kc::KrylovConstructor; memory = 20)
```

`memory` is set to `n` if the value given is larger than `n`.
