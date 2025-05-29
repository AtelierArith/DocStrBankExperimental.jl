Workspace for the in-place method [`lsqr!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = LsqrWorkspace(m, n, S)
workspace = LsqrWorkspace(A, b)
workspace = LsqrWorkspace(kc::KrylovConstructor)
```
