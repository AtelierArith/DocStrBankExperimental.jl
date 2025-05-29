Workspace for the in-place method [`gpmr!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = GpmrWorkspace(m, n, S; memory = 20)
workspace = GpmrWorkspace(A, b; memory = 20)
workspace = GpmrWorkspace(kc::KrylovConstructor; memory = 20)
```

`memory` is set to `n + m` if the value given is larger than `n + m`.
