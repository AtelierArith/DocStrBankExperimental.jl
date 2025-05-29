Workspace for the in-place method [`diom!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = DiomWorkspace(m, n, S; memory = 20)
workspace = DiomWorkspace(A, b; memory = 20)
workspace = DiomWorkspace(kc::KrylovConstructor; memory = 20)
```

`memory` is set to `n` if the value given is larger than `n`.
