Workspace for the in-place method [`cgls!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = CglsWorkspace(m, n, S)
workspace = CglsWorkspace(A, b)
workspace = CglsWorkspace(kc::KrylovConstructor)
```
