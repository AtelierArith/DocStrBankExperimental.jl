Workspace for the in-place method [`bilqr!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = BilqrWorkspace(m, n, S)
workspace = BilqrWorkspace(A, b)
workspace = BilqrWorkspace(kc::KrylovConstructor)
```
