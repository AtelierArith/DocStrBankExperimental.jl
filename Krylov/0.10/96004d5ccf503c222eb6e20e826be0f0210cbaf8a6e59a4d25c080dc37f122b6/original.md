Workspace for the in-place method [`trilqr!`](@ref).

The following outer constructors can be used to initialize this workspace:

```
workspace = TrilqrWorkspace(m, n, S)
workspace = TrilqrWorkspace(A, b)
workspace = TrilqrWorkspace(kc::KrylovConstructor)
```
