Workspace for the in-place method [`fom!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = FomWorkspace(m, n, S; memory = 20)
workspace = FomWorkspace(A, b; memory = 20)
workspace = FomWorkspace(kc::KrylovConstructor; memory = 20)
```

`memory` is set to `n` if the value given is larger than `n`.
