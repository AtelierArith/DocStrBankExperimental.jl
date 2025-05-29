Workspace for the in-place method [`lsmr!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = LsmrWorkspace(m, n, S)
workspace = LsmrWorkspace(A, b)
workspace = LsmrWorkspace(kc::KrylovConstructor)
```
